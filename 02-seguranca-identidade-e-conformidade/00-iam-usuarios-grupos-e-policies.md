# 🔐 IAM: Usuários, Grupos e Policies

O **IAM (Identity and Access Management)** é o serviço responsável por controlar quem pode acessar sua conta AWS e quais ações cada identidade pode realizar.

Se a AWS fosse um prédio corporativo:

- **Autenticação** responde à pergunta: **Quem é você?**
- **Autorização** responde à pergunta: **O que você pode fazer?**

> **Importante:** O IAM é um **serviço global (Global Service)**. As configurações realizadas nele são válidas para toda a conta AWS, independentemente da Região.

Além disso, o IAM é um serviço **gratuito**.

---

## IAM resolve dois problemas fundamentais

### Autenticação (Authentication)

Verifica a identidade do usuário.

Exemplos:

- Usuário e senha
- Access Keys
- Multi-Factor Authentication (MFA)

### Autorização (Authorization)

Define quais recursos o usuário pode acessar e quais ações pode executar.

Exemplos:

- Criar instâncias EC2
- Ler objetos do Amazon S3
- Criar bancos de dados RDS

---

## 1. IAM User (Usuário)

Um **IAM User** representa uma identidade única dentro da sua conta. Pode ser uma pessoa (você ou um colega de time) ou uma aplicação que precise interagir com a AWS.

*   **Credenciais de Longo Prazo:** Diferente de acessos temporários, o usuário tem credenciais persistentes, como senha para o console ou **Access Keys** para uso via CLI/API.
*   **Default:** Por padrão, um usuário novo nasce com **zero permissões** (Implicit Deny). Ele não faz nada até você dar o poder a ele.

### Características

- Possui credenciais permanentes (Long-Term Credentials).
- Pode acessar o Console AWS utilizando usuário e senha.
- Pode utilizar Access Keys para CLI e SDKs.
- Nasce sem permissões.

> **Importante:** Todo novo usuário possui **Implicit Deny**, ou seja, nenhuma ação é permitida até que alguma Policy seja anexada.

---

## 2. IAM Group (Grupo)

Gerenciar permissões usuário por usuário é um "trabalho de corno" que não escala. É aí que entram os **IAM Groups**.

*   **Herança de Permissões:** Você cria um grupo (ex: `Admins`, `Developers`, `Testes`), anexa as permissões ao grupo e joga os usuários lá dentro. Eles herdam tudo automaticamente.
*   **Vantagem:** Se um dev sai do time de testes e vai para o de produção, você só muda ele de grupo. O acesso antigo some e o novo aparece na hora.

### Funcionamento

1. Cria-se o grupo.
2. Anexa-se uma Policy ao grupo.
3. Adicionam-se usuários.

Todos os usuários herdam automaticamente as permissões do grupo.

### Regras importantes

- Um grupo pode possuir vários usuários.
- Um usuário pode participar de vários grupos.
- Um grupo **não pode conter outro grupo**.

Não existe aninhamento de grupos no IAM.

---

## 3. IAM Policies (Políticas)

As **Policies** são o coração da autorização. Elas são documentos em formato **JSON** que dizem explicitamente o que é permitido ou negado.

Uma Policy básica foca em três pilares (Bloco `Statement`):

| Campo | Função |
|--------|---------|
| Effect | Pode ser `Allow` (Permitir) ou `Deny` (Negar). |
| Action | O que pode ser feito (ex: `s3:ListBucket`, `ec2:RunInstances`). |
| Resource | Em qual recurso isso se aplica (ex: um bucket específico ou `*` para todos). |

Exemplo conceitual:

```json
{
  "Effect": "Allow",
  "Action": "s3:GetObject",
  "Resource": "arn:aws:s3:::meu-bucket/*"
}
```

Nesse exemplo:

- **Effect:** Permite.
- **Action:** Ler objetos do S3.
- **Resource:** Apenas objetos do bucket especificado.

### Estrutura PARC

Uma forma simples de memorizar a estrutura lógica das Policies é utilizar o acrônimo **PARC**.

| Letra | Significado |
|--------|-------------|
| **P** | Principal (quem executa) |
| **A** | Action (o que pode fazer) |
| **R** | Resource (em qual recurso) |
| **C** | Condition (em quais condições) |

Exemplo de Condition:

- Permitir apenas se o usuário possuir MFA ativo.
- Permitir apenas durante horário comercial.
- Permitir apenas a partir de determinado endereço IP.

---

## 4. Princípio do Menor Privilégio (Principle of Least Privilege)

Este é o mantra que você vai levar para a vida e para a prova. O **Princípio do Menor Privilégio** dita que você deve dar ao usuário **apenas o acesso mínimo necessário** para ele realizar o trabalho dele, e nada mais.

Nunca forneça permissões administrativas quando uma permissão específica atende ao requisito.

Se o cara só precisa ler arquivos de um bucket, não dê permissão de `AdministratorAccess`. Dê apenas `s3:GetObject` naquele bucket específico. Isso limita o "blast radius" (raio de explosão) caso a conta dele seja comprometida.

Esse conceito reduz significativamente o impacto caso uma credencial seja comprometida.

### Boas Práticas

- Utilize grupos para organizar permissões.
- Evite permissões administrativas desnecessárias.
- Sempre siga o Princípio do Menor Privilégio.
- Utilize MFA para usuários humanos.
- Utilize Policies específicas em vez de permissões amplas (`*`).

---

## 🎯 Gatilhos de Exame

Se esses termos aparecerem no enunciado, você já sabe para onde olhar:

| Termo | Significado |
|--------|-------------|
| Identity and Access Management (IAM) | Serviço global de controle de acesso. |
| Authentication | Quem é o usuário |
| Authorization | O que o usuário pode fazer |
| IAM User | Identidade individual e persistente para pessoas ou apps (Long-term credentials). |
| IAM Group | Coleção de usuários; facilita a gestão por herança. |
| IAM Policy | Documento JSON de permissões. |
| Allow | Permitir ação |
| Deny | Negar ação |
| Implicit Deny | Sem Policy, nada é permitido |
| Effect, Action, Resource | Os blocos essenciais da permissão. |
| Principle of Least Privilege | Prática de dar o acesso mínimo necessário |
| Global Service | Funciona para toda a conta AWS. IAM não depende de região. |

> **Pegadinha de Simulado:** A AWS gerencia a segurança física do IAM, mas **você** (cliente) é o responsável por criar os usuários, gerenciar as senhas, habilitar o MFA e aplicar as políticas corretamente. É segurança **NA** nuvem!

---

## ⚠️ Dicas de Prova

- O IAM é um **serviço global**, não regional.
- Usuários novos **não possuem nenhuma permissão**.
- Grupos **não podem conter outros grupos**.
- Policies são escritas em **JSON**.
- Uma permissão **Deny explícita** sempre prevalece sobre uma permissão **Allow**.
- O menor privilégio é uma das práticas de segurança mais cobradas na certificação AWS CLF-C02.

---
---