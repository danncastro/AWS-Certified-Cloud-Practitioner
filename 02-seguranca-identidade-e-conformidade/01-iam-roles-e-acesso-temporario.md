# 🔐 IAM Roles e Acesso Temporário: A Segurança Dinâmica

Se os **IAM Users** são as identidades fixas da sua Enquanto um **IAM User** representa uma identidade permanente, uma **IAM Role** representa uma identidade temporária, utilizada por usuários, aplicações ou serviços AWS para executar tarefas específicas com segurança.

O uso de Roles elimina a necessidade de armazenar credenciais permanentes em aplicações e é considerado uma das principais boas práticas de segurança na AWS.

---

## 1. O Conceito de IAM Role (Função)

Uma **IAM Role** é uma identidade que você cria na sua conta com permissões específicas, mas que **NÃO possui senhas ou chaves de acesso (Access Keys) de longo prazo**. 

Pense em uma Role como um crachá temporário entregue para realizar uma atividade específica. Terminada a tarefa, o crachá perde a validade automaticamente

*   **Não é persistente:** Você não faz "login" em uma Role. Você a **assume**.
*   **Identidade para serviços:** É a forma primária de dar permissões para recursos (como uma instância EC2 ou uma função Lambda) sem embutir credenciais neles.


Após ser assumida, a AWS gera credenciais temporárias que permitem executar determinadas ações durante um período limitado.

---

### Características de uma IAM Role

- Não possui senha.
- Não possui Access Keys permanentes.
- Pode ser assumida por usuários ou serviços.
- Utiliza credenciais temporárias.
- É amplamente utilizada em arquiteturas modernas na AWS.

---

## 2. Acesso Temporário: O Papel do AWS STS

Por trás de cada Role, existe um serviço de segurança fundamental: o **AWS STS (Security Token Service)**. O STS é responsável por emitir as credenciais temporárias utilizadas durante a sessão.

O STS gera **Temporary security credentials** (credenciais de segurança temporárias). Quando alguém executa um **AssumeRole**, o fluxo acontece da seguinte forma:

1. Usuário ou serviço solicita assumir uma Role.
2. O STS valida a solicitação.
3. O STS gera credenciais temporárias.
4. Essas credenciais são utilizadas para acessar os serviços autorizados.

As credenciais temporárias são compostas por:

- Access Key ID
- Secret Access Key
- Session Token

---

### Vantagens Reais

#### Expiração automática 

As credenciais possuem tempo de vida limitado. Elas duram de poucos minutos a algumas horas e depois morrem sozinhas.

> Isso reduz significativamente o risco de comprometimento.

---

#### Maior segurança - Zero Leakage

Como não existem chaves permanentes armazenadas:

- Não há Access Keys gravadas em arquivos.
- Não há senhas embutidas no código.
- Não há necessidade de distribuir credenciais entre servidores.

Mesmo que uma credencial seja interceptada, ela deixará de funcionar após sua expiração.

~~~mermaid
sequenceDiagram
    participant App as Aplicação (EC2/Lambda)
    participant STS as AWS STS
    participant S3 as Amazon S3
    
    App->>STS: Solicita acesso (AssumeRole)
    STS-->>App: Entrega Credenciais Temporárias (Token)
    App->>S3: Faz a requisição usando o Token
    S3->>S3: Valida se o Token é válido e permitido
    S3-->>App: Entrega o dado solicitado
~~~

---

## 3. Cenários Clássicos de Uso (Gabarito de Prova)

A AWS cobra Roles em três cenários principais que você precisa identificar no enunciado:

---

### A) Aplicações em EC2 (EC2 Instance Profile) acessando o Amazon S3

Uma aplicação hospedada em uma instância EC2 precisa acessar um bucket S3.

---

#### ❌ Maneira incorreta

- Criar um IAM User.
- Gerar Access Keys.
- Salvar as chaves no código da aplicação (config.ini).

Problemas:

- Vazamento de credenciais.
- Rotação manual.
- Alto risco de segurança.

---

#### ✅ Maneira correta

- Criar uma IAM Role com acesso ao S3.
- Conceder permissões ao S3.
- Associar essa Role à instância EC2 através de um **Instance Profile**.

A própria instância obtém automaticamente as credenciais temporárias através do STS.

Nenhuma Access Key precisa ser armazenada.

---

#### EC2 Instance Profile

O **Instance Profile** é o mecanismo utilizado para anexar uma IAM Role a uma instância EC2.

A aplicação consulta automaticamente o serviço de metadados da instância para obter credenciais temporárias.

Não existe configuração manual de chaves.

---

### B) Acesso Cross-Account

A conta de Auditoria (Conta A) precisa ler logs da conta de Produção (Conta B).

Um cenário muito comum ocorre quando uma conta AWS precisa acessar recursos de outra conta.

Exemplo:

- Conta A → Auditoria
- Conta B → Produção

A Conta B cria uma Role permitindo que usuários da Conta A possam assumi-la.

O usuário da Conta A assume essa Role temporariamente para realizar a auditoria sem precisar de um usuário fixo 
na outra conta.

~~~mermaid
flowchart LR

    subgraph A["🏢 Conta AWS A"]
        U[👤 Usuário]
    end

    STS["🔐 AWS STS"]

    subgraph B["🏢 Conta AWS B"]
        ROLE[🛡️ IAM Role]
        TEMP[🎫 Credenciais Temporárias]
        RES[☁️ Recursos AWS]
    end

    U -->|AssumeRole| STS
    STS --> ROLE
    ROLE --> TEMP
    TEMP --> RES
~~~

> Não é necessário criar usuários duplicados em cada conta.

---

### C) Federação de Identidades (Identity Federation)

Seus funcionários já fazem login no Active Directory da empresa ou no Google. Você não quer criar 500 usuários no IAM de novo.

Muitas empresas já utilizam provedores de identidade corporativos.

Exemplos:

- Microsoft Active Directory
- Microsoft Entra ID (Azure AD)
- Google Workspace
- Okta

Nesses casos, não faz sentido criar centenas de usuários IAM.

A solução é utilizar **Identity Federation**.

O usuário realiza login utilizando sua identidade corporativa e recebe uma Role temporária na AWS.

O serviço atualmente recomendado para esse cenário é o **AWS IAM Identity Center**.

O AWS IAM Identity Center permite que esses usuários externos façam login com suas credenciais corporativas e assumam uma Role específica dentro da AWS.

---

## 4. IAM User vs. IAM Role: O Duelo
Não caia nas pegadinhas da banca. Memorize as diferenças:

| Característica | IAM User | IAM Role |
|----------------|----------|-----------|
| Destinado para | Pessoas ou sistemas legados | Serviços AWS, aplicações e usuários externos |
| Credenciais | Longo prazo (Senha / Access Keys fixas). | Curto prazo (STS / Tokens dinâmicos). |
| Acesso | Permanentes (sempre ativo) | Temporárias (precisa assumir a função) |
| Risco | Alto (chaves podem vazar/ser esquecidas). | Baixo (as chaves expiram sozinhas). |
| STS | Não | Sim |
| Segurança | Menor | Maior |
| Boa prática AWS | Apenas quando necessário | Sempre que possível |

---

### Quando utilizar IAM Role?

Utilize Roles sempre que:

- Uma instância EC2 precisar acessar outro serviço AWS.
- Uma função Lambda acessar DynamoDB ou S3.
- Um container ECS acessar Secrets Manager.
- Um Pod no EKS acessar recursos AWS (IRSA).
- Uma conta AWS acessar outra conta.
- Usuários corporativos acessarem a AWS via Federação.

---

### Benefícios das IAM Roles

- Elimina Access Keys permanentes.
- Credenciais expiram automaticamente.
- Facilita rotação de credenciais.
- Reduz risco de vazamento.
- Permite acesso entre contas AWS.
- Implementa facilmente o Princípio do Menor Privilégio.

---

## 🎯 Gatilho de Exame
Se você ler estes termos em inglês, a resposta é IAM Role:

| Termo | Significado |
|--------|-------------|
| IAM Role | Identidade temporária |
| AssumeRole | Assumir uma Role |
| AWS STS | Gera credenciais temporárias |
| Temporary Security Credentials | Access Key temporária + Secret + Session Token |
| EC2 Instance Profile | O "contêiner" que permite anexar a Role as EC2. |
| Cross-Account Access | Delegar acesso entre contas AWS diferentes |
| Identity Federation | Login usando identidade externa (AD, SAML 2.0). |
| IAM Identity Center | Federação de identidades na AWS |
| Least Privilege | Conceder apenas o acesso necessário |

---

## ⚠️ Pegadinhas de Prova

- **IAM Roles não possuem senha.**
- **IAM Roles não possuem Access Keys permanentes.**
- Quem gera as credenciais temporárias é o **AWS STS**.
- Aplicações executando em **EC2** devem utilizar **IAM Roles**, nunca Access Keys armazenadas no código.
- **Cross-Account Access** é implementado utilizando **IAM Roles**.
- **Identity Federation** também utiliza Roles para conceder acesso temporário.
- Sempre que a questão mencionar **Temporary Security Credentials**, **AssumeRole** ou **STS**, a resposta provavelmente envolve **IAM Roles**.
- Para aplicações na AWS, a melhor prática é **não armazenar credenciais**, mas utilizar **IAM Roles** sempre que possível.

---

## 🚨 Sinal de Alerta: 

> **A prova pode perguntar:** "Qual a melhor forma de uma aplicação em EC2 acessar o S3?". 
>
> Se uma opção sugerir criar chaves de acesso fixas, ela está ***ERRADA.*** A resposta vencedora sempre envolverá ***IAM Roles.***

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ IAM: Usuários, Grupos e Policies](01-iam-roles-e-acesso-temporario.md)
* [➡️ Autenticação, MFA e Conta root](02-autenticacao-mfa-e-conta-root.md)

---
---