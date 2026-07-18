# 🔐 Autenticação, MFA e Conta Root: Protegendo as Chaves do Reino

Quando uma conta AWS é criada, automaticamente é criado o **AWS Account Root User**.

Essa identidade possui acesso irrestrito a toda a conta e deve ser utilizada apenas em situações excepcionais.

Proteger a conta Root é uma das práticas de segurança mais importantes da AWS e um dos assuntos mais cobrados na certificação CLF-C02. Se alguém rouba essa credencial, sua infraestrutura, seus dados e o cartão de crédito da empresa já eram. Proteger esse acesso não é opcional, é sobrevivência básica de engenharia.

---

## 1. O Usuário Root da Conta ( God Mode )

O **AWS Account Root User** é a identidade criada automaticamente no momento em que você abre a conta, usando seu endereço de e-mail. 

*   **Poder Irrestrito:** Ele tem acesso completo e total a absolutamente **todos** os recursos e informações de faturamento da conta.
*   **Imune a Policies:** Diferente de um usuário administrador do IAM, o poder do Root **não pode ser limitado** por nenhuma política do IAM (IAM Policy). Ele sempre terá a palavra final.
*   **Risco Máximo:** Como o acesso é absoluto, ele é o alvo número 1 de ataques. 

> O usuário Root sempre possui privilégios máximos, independentemente das políticas IAM existentes.

---

### Por que o Root é tão perigoso?

Se um invasor obtiver acesso à conta Root, ele poderá:

- Excluir recursos.
- Criar recursos caros.
- Alterar configurações de segurança.
- Acessar dados confidenciais.
- Alterar informações de pagamento.
- Encerrar a conta AWS.

Por isso, a AWS recomenda utilizar o Root apenas quando absolutamente necessário.

---

## 2. Melhores Práticas de Segurança (Regras de Ouro)

Para não ser o dev que deixou a empresa na mão, siga este checklist exaustivamente cobrado no exame:

*   **Nunca criar Access Keys:** Nunca crie chaves de acesso (Access Key ID / Secret Access Key) para o usuário Root. Se elas existirem, a recomendação **deleta-las imediatamente**. Aplicações nunca devem utilizar credenciais do Root.
Para acesso programático, utilize **IAM Roles**.
*   **Utilizar uma senha forte:** Use uma senha extremamente forte, complexa e que não seja repetida em nenhum outro lugar.
*   **Uso Mínimo:** Pare de usar a conta Root para tarefas diárias imediatamente, após criar o primeiro usuário administrativo no IAM. Ative o MFA e guarde o Root apenas para emergências ou tarefas exclusivas.
*   **MFA Obrigatório:** Esta é uma das primeiras recomendações da AWS. Ative a Autenticação de Múltiplos Fatores no Root antes de qualquer outra coisa.

> O Multi-Factor Authentication adiciona uma camada extra de proteção contra roubo de credenciais.

---

## 3. Multi-Factor Authentication (MFA)

O **MFA** adiciona uma camada extra de proteção conhecida como "defesa em profundidade". Ele exige dois fatores para o login:
1.  **Algo que você sabe:** Exemplo, *sua senha*.
2.  **Algo que você possui:** Aplicativo autenticador, um dispositivo físico ou digital que gera um token.

> Mesmo que a senha seja descoberta, o invasor ainda precisará do segundo fator para acessar a conta.

---

### Tipos de MFA suportados:
*   **Virtual MFA:** Aplicativos autenticadores no celular (ex: Google Authenticator, Authy). É a opção mais comum e rápida.
*   **Chave de Segurança FIDO/U2F:** Dispositivos físicos conectados via USB ou NFC (ex: YubiKey).
*   **Token de Hardware:** Dispositivos físicos que geram códigos temporários de seis dígitos. (TOTP).

---

### Quando utilizar a Conta Root?

Na prática, quase nunca.

O Root deve ser utilizado apenas quando a operação exigir privilégios exclusivos.

---

## 4. O que APENAS o Usuário Root consegue fazer?

A AWS ama perguntar isso para testar se você sabe quando o Root é realmente necessário. Ações exclusivas incluem:

*   **Encerrar a conta AWS:** Ninguém mais tem esse poder.
*   **Alterar planos de suporte:** Mudar do Business para o Enterprise, por exemplo.
*   **Configurações de faturamento consolidadas:** Gerenciar a conta pagadora no AWS Organizations.
*   **MFA Delete no S3:** Configurar um bucket para exigir MFA na hora de deletar arquivos.
*   **Alterar dados cadastrais:** Mudar o e-mail ou a própria senha mestre do root.
*   **Restaurar permissões de admin:** Recuperar acesso administrativo caso todas as permissões IAM sejam perdidas.

---

## Fluxo recomendado após criar uma conta AWS

~~~mermaid
flowchart TD

    subgraph ROOT["👑 Configuração Inicial (Root User)"]
        A([Criar Conta AWS])
        B[Entrar como Root]
        C[Ativar MFA]
        D[Criar Usuário Administrador IAM]

        A --> B --> C --> D
    end

    subgraph IAM["👤 Operação Diária (IAM User)"]
        E[Realizar atividades administrativas]
        F([Conta Root utilizada apenas em emergências])

        E --> F
    end

    D --> E
~~~

---

### Root × IAM User

| Característica | Root | IAM User |
|----------------|------|----------|
| Criado automaticamente | ✅ | ❌ |
| Login por e-mail | ✅ | ❌ |
| Possui permissões totais | ✅ | ❌ |
| Pode ser limitado por IAM Policy | ❌ | ✅ |
| Uso diário recomendado | ❌ | ✅ |
| Deve possuir MFA | ✅ Obrigatório | ✅ Recomendado |

---

### Boas Práticas de Segurança

- Ative MFA imediatamente.
- Nunca utilize o Root para atividades do dia a dia.
- Nunca crie Access Keys para o Root.
- Crie um usuário administrador IAM.
- Utilize o Princípio do Menor Privilégio.
- Utilize IAM Roles para aplicações.
- Monitore acessos com CloudTrail.

---


## 🎯 Gatilho de Exame

Mapeie esses termos para não cair em pegadinha:

| Termo | Significado |
|--------|-------------|
| AWS Account Root User | O dono absoluto da conta, login via e-mail. |
| Root Credentials | Devem ser protegidas e **nunca** usadas para o dia a dia. |
| Multi-Factor Authentication (MFA) | Senha + segundo fator |
| Virtual MFA | Aplicativo autenticador |
| Hardware MFA | Token físico |
| Root Access Keys | Devem ser evitadas/removidas |
| Protect Root Account | Sinônimo de "Ativar MFA e usar senhas fortes". |
| Least Privilege | Utilizar usuários IAM em vez do Root |
| Delete root access keys | Ação mandatória de segurança inicial |

> **Sinal de Alerta:** Se a questão perguntar qual a primeira coisa a fazer em uma conta nova, a resposta vencedora quase sempre envolve **Ativar MFA na conta Root** ou **Criar um usuário administrador no IAM**.

---

## ⚠️ Pegadinhas de Prova

- O **Root não pode ser restringido por IAM Policies**.
- O **Root deve ser utilizado apenas em situações excepcionais**.
- A primeira ação recomendada após criar uma conta AWS é **ativar o MFA na conta Root**.
- Em seguida, deve-se **criar um usuário administrador IAM** para o uso diário.
- Nunca utilize **Access Keys** no usuário Root.
- Sempre que a prova mencionar **proteger a conta Root**, pense imediatamente em:
  - MFA
  - Senha forte
  - Não utilizar no dia a dia
  - Não criar Access Keys

---

* [🏠 Menu Principal](../README.md)
* [⬅️ IAM Roles e Acesso Temporário](01-iam-roles-e-acesso-temporario.md)
* [➡️ Proteção Contra DDoS, Shield & WAF](03-protecao-contra-ddos-shield-e-waf.md)