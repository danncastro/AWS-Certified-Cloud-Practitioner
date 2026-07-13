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

### Vantagens Reais

#### Expiração automática 

As credenciais possuem tempo de vida limitado. Elas duram de poucos minutos a algumas horas e depois morrem sozinhas.

> Isso reduz significativamente o risco de comprometimento.

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

### A) Aplicações em EC2 (EC2 Instance Profile) acessando o Amazon S3

Uma aplicação hospedada em uma instância EC2 precisa acessar um bucket S3.

#### ❌ Maneira incorreta

- Criar um IAM User.
- Gerar Access Keys.
- Salvar as chaves no código da aplicação (config.ini).

Problemas:

- Vazamento de credenciais.
- Rotação manual.
- Alto risco de segurança.

#### ✅ Maneira correta

- Criar uma IAM Role com acesso ao S3.
- Conceder permissões ao S3.
- Associar essa Role à instância EC2 através de um **Instance Profile**.

A própria instância obtém automaticamente as credenciais temporárias através do STS.

Nenhuma Access Key precisa ser armazenada.

#### EC2 Instance Profile

O **Instance Profile** é o mecanismo utilizado para anexar uma IAM Role a uma instância EC2.

A aplicação consulta automaticamente o serviço de metadados da instância para obter credenciais temporárias.

Não existe configuração manual de chaves.


### B) Acesso Cross-Account

A conta de Auditoria (Conta A) precisa ler logs da conta de Produção (Conta B).

Um cenário muito comum ocorre quando uma conta AWS precisa acessar recursos de outra conta.

Exemplo:

- Conta A → Auditoria
- Conta B → Produção

A Conta B cria uma Role permitindo que usuários da Conta A possam assumi-la.

    Solução: A Conta B cria uma Role que "confia" na Conta A. O usuário da Conta A assume essa Role temporariamente para realizar a auditoria sem precisar de um usuário fixo na outra conta.

C. Federação de Identidades (Identity Federation)
Seus funcionários já fazem login no Active Directory da empresa ou no Google. Você não quer criar 500 usuários no IAM de novo.

    Solução: O AWS IAM Identity Center permite que esses usuários externos façam login com suas credenciais corporativas e assumam uma Role específica dentro da AWS.

---

4. IAM User vs. IAM Role: O Duelo
Não caia nas pegadinhas da banca. Memorize as diferenças:
Critério
	
IAM User
	
IAM Role
Público
	
Humanos ou sistemas legados fixos.
	
Serviços AWS, aplicações ou usuários externos.
Credenciais
	
Longo prazo (Senha / Access Keys fixas).
	
Curto prazo (STS / Tokens dinâmicos).
Acesso
	
Persistente (sempre ativo).
	
Temporário (precisa assumir a função).
Risco
	
Alto (chaves podem vazar/ser esquecidas).
	
Baixo (as chaves expiram sozinhas).
🎯 Gatilho de Exame
Se você ler estes termos em inglês, a resposta é IAM Role:

    Temporary security credentials: Pista direta para Roles e STS.
    Cross-account access: Delegar acesso entre contas AWS diferentes.
    Federation / Federated identity: Usuários externos acessando a AWS (AD, SAML 2.0).
    Assume a role: O verbo de ação para usar uma Role.
    EC2 instance profile: O "contêiner" que permite anexar a Role à máquina virtual.
    Least Privilege: Roles ajudam a aplicar o privilégio mínimo ao dar acesso apenas pelo tempo necessário.

Sinal de Alerta: A prova pode perguntar: "Qual a melhor forma de uma aplicação em EC2 acessar o S3?". Se uma opção sugerir criar chaves de acesso fixas, ela está ERRADA. A resposta vencedora sempre envolverá IAM Roles.