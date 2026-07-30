# Síntese IAM: User vs. Group vs. Role

Depois de estudar **IAM Users**, **IAM Groups** e **IAM Roles** separadamente, chega a hora da comparação que mais aparece na prova da CLF-C02.

A AWS costuma criar cenários onde mais de uma alternativa parece funcionar, mas apenas uma segue corretamente as boas práticas de segurança e o **Princípio do Menor Privilégio (Least Privilege)**.

O segredo é identificar **quem precisa do acesso**, **por quanto tempo** e **como esse acesso será utilizado**.

---

## 1. Tabela Comparativa Definitiva

Bata o olho nesta tabela para diferenciar rapidamente cada entidade do IAM.

| Característica | IAM User | IAM Group | IAM Role |
|----------------|----------|-----------|----------|
| **Quem é?** | Identidade única (pessoa ou aplicação). | Coleção lógica de usuários IAM. | Identidade assumida temporariamente. |
| **Credenciais** | Senha e/ou Access Keys permanentes. | Não possui credenciais. | Credenciais temporárias via AWS STS. |
| **Acesso ao Console** | Sim | Não | Não diretamente (precisa assumir a Role). |
| **Uso Principal** | Usuários humanos e sistemas legados. | Organizar permissões de vários usuários. | Serviços AWS, aplicações e acesso temporário. |
| **Tempo de Acesso** | Longo prazo | Herdado dos usuários | Curto prazo |
| **Pode possuir Policies?** | Sim | Sim | Sim |
| **Exemplo** | Desenvolvedor acessando a conta AWS. | Grupo Developers. | EC2 acessando um bucket S3. |

---

## 2. Entendendo a Diferença

Embora todos façam parte do IAM, cada um possui um objetivo completamente diferente.

### IAM User

Representa uma identidade individual.

Normalmente corresponde a uma pessoa da equipe ou a um sistema legado que necessita de credenciais permanentes para acessar a AWS.

Características:

- possui login no Console;
- pode possuir Access Keys;
- normalmente pertence a um ou mais grupos;
- pode receber Policies diretamente.

---

### IAM Group

Serve apenas para organizar usuários.

Em vez de conceder permissões individualmente para dezenas de pessoas, basta criar um grupo e anexar as Policies nele.

Todos os usuários pertencentes ao grupo herdam automaticamente essas permissões.

Características:

- não possui login;
- não possui Access Keys;
- não representa uma identidade;
- apenas agrupa usuários.

---

### IAM Role

É uma identidade temporária utilizada quando alguém ou algum serviço precisa assumir permissões durante um período limitado.

Não possui senha nem Access Keys permanentes.

Quando uma Role é assumida, o **AWS STS (Security Token Service)** fornece credenciais temporárias que expiram automaticamente.

É a forma recomendada para permitir que serviços AWS acessem outros serviços AWS.

---

## 3. Quando utilizar cada um?

Essa é uma dúvida extremamente comum.

### Use IAM User quando...

- uma pessoa precisa acessar a conta AWS;
- um sistema legado necessita de credenciais permanentes;
- é necessário acesso programático de longo prazo.

---

### Use IAM Group quando...

- vários usuários precisam das mesmas permissões;
- deseja facilitar a administração de acessos;
- quer seguir boas práticas de gerenciamento.

---

### Use IAM Role quando...

- uma EC2 precisa acessar um bucket S3;
- uma função Lambda precisa acessar um DynamoDB;
- existe acesso entre contas AWS (*Cross-Account*);
- usuários externos utilizam Federação de Identidades;
- deseja eliminar Access Keys fixas.

---

## 4. Regras de Ouro para Decisão

Durante a prova, algumas palavras praticamente entregam a resposta.

| Se aparecer... | Resposta |
|----------------|----------|
| Temporary credentials | IAM Role |
| Assume Role | IAM Role |
| AWS STS | IAM Role |
| EC2 Instance Profile | IAM Role |
| Cross-account access | IAM Role |
| Identity Federation | IAM Role |
| Grupo de desenvolvedores | IAM Group |
| Mesmas permissões para vários usuários | IAM Group |
| Long-term credentials | IAM User |
| Access Keys | IAM User |

---

## 5. Restrições Importantes

Existem algumas limitações que aparecem frequentemente nas pegadinhas da prova.

### Grupos não podem conter outros grupos

O IAM **não permite grupos aninhados**.

Um grupo pode conter diversos usuários, mas nunca outro grupo.

---

### Grupos não fazem login

Quem faz login é sempre um **IAM User**.

O grupo existe apenas para organizar permissões.

---

### Roles não possuem senha

Uma Role nunca possui:

- senha;
- Access Key permanente;
- usuário associado.

Ela sempre precisa ser **assumida (Assume Role)** para gerar credenciais temporárias.

---

### Roles não substituem usuários

Embora um usuário possa assumir uma Role, isso não significa que Roles substituem usuários.

Normalmente:

- Usuários → acesso diário.
- Roles → acesso temporário.

---

## 6. Exemplos Clássicos de Prova

### Cenário 1

> Cem desenvolvedores precisam exatamente das mesmas permissões.

**Resposta:**

IAM Group.

---

### Cenário 2

> Uma aplicação rodando em uma instância EC2 precisa acessar um bucket S3.

**Resposta:**

IAM Role.

---

### Cenário 3

> Um desenvolvedor precisa acessar o Console AWS diariamente.

**Resposta:**

IAM User.

---

### Cenário 4

> Uma empresa utiliza Active Directory para autenticação.

**Resposta:**

IAM Role (Federação de Identidades).

---

### Cenário 5

> Uma aplicação utiliza Access Keys gravadas no código.

**Resposta:**

Não é uma boa prática.

O correto é utilizar uma **IAM Role**.

---

## IAM User vs Group vs Role

| Recurso | User | Group | Role |
|----------|------|-------|------|
| Representa identidade | ✅ | ❌ | ✅ |
| Possui senha | ✅ | ❌ | ❌ |
| Possui Access Keys permanentes | ✅ | ❌ | ❌ |
| Recebe Policies | ✅ | ✅ | ✅ |
| Acesso temporário | ❌ | ❌ | ✅ |
| Utiliza AWS STS | ❌ | ❌ | ✅ |
| Organiza usuários | ❌ | ✅ | ❌ |
| Ideal para serviços AWS | ❌ | ❌ | ✅ |

---

## Mnemônico

### User → Pessoa

Pense em:

- Login
- Senha
- Access Keys

---

### Group → Organização

Pense em:

- Usuários
- Permissões compartilhadas
- Administração simplificada

---

### Role → Permissão Temporária

Pense em:

- AWS STS
- Assume Role
- Credenciais temporárias
- Serviços AWS

---

## 🎯 Gatilhos de Exame

Se aparecer...

| Enunciado | Resposta |
|------------|----------|
| Long-term credentials | IAM User |
| Access Keys | IAM User |
| Interactive access | IAM User |
| Multiple users with same permissions | IAM Group |
| Inherited permissions | IAM Group |
| No nested groups | IAM Group |
| Temporary credentials | IAM Role |
| AWS STS | IAM Role |
| Assume Role | IAM Role |
| Cross-account access | IAM Role |
| Identity Federation | IAM Role |
| EC2 Instance Profile | IAM Role |

---

## Pegadinhas da Prova

| Se a questão perguntar... | Resposta |
|----------------------------|----------|
| Quem faz login na AWS? | IAM User |
| Quem organiza usuários? | IAM Group |
| Quem fornece acesso temporário? | IAM Role |
| Quem utiliza AWS STS? | IAM Role |
| Grupo pode conter outro grupo? | ❌ Não |
| Role possui senha? | ❌ Não |
| EC2 deve utilizar Access Keys? | ❌ Não, utilize IAM Role |

---

> **💡 Dica de Ouro:** Sempre pense na seguinte sequência: **Pessoa → User. Equipe → Group. Serviço ou acesso temporário → Role.** Se a questão mencionar **STS**, **Assume Role**, **EC2**, **Lambda** ou **Cross-Account**, praticamente sempre a resposta será **IAM Role**.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Central de segurança (Security Hub)](10-central-de-seguranca-security-hub.md)
* [➡️ Mnemonico - Watch vs Trail vs Config](12-mnemonico-watch-trail-config.md)

---
---