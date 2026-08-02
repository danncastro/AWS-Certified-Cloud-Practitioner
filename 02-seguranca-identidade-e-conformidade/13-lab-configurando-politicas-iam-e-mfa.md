# Lab: Configurando Políticas IAM e MFA

Dcorar definição de IAM para a prova é fácil. O difícil é entender **como as peças se encaixam na prática**.

Na AWS, praticamente tudo gira em torno de **identidade, autenticação e autorização**. Antes de uma pessoa ou aplicação acessar qualquer recurso, a AWS precisa responder três perguntas:

- **Quem está tentando acessar?** → Identidade (**IAM User, Role ou Federation**)
- **O que essa identidade pode fazer?** → Permissões (**IAM Policy**)
- **Como esse acesso está protegido?** → Segurança adicional (**MFA**)

Neste laboratório vamos montar um cenário real:

Um desenvolvedor precisa acessar a AWS, mas seguindo uma regra de segurança:

> "Esse usuário pode apenas visualizar arquivos de um bucket específico do S3. Nada além disso."

Esse é exatamente o conceito de **Princípio do Menor Privilégio (Least Privilege)**, um dos temas mais cobrados na certificação AWS Cloud Practitioner.

---

# 1. Objetivos do Lab

Ao final deste laboratório, você será capaz de:

- Criar um **IAM User** com acesso ao Console AWS.
- Organizar permissões utilizando um **IAM Group**.
- Criar uma **IAM Policy personalizada utilizando JSON**.
- Aplicar permissões seguindo o princípio do menor privilégio.
- Configurar um dispositivo **MFA Virtual**.
- Validar permissões permitidas e bloqueadas.

---

# 2. Cenário do Laboratório

Imagine uma empresa onde existe um time de desenvolvimento.

Esse time precisa consultar arquivos armazenados no Amazon S3, porém os desenvolvedores não devem:

- Excluir arquivos.
- Criar novos buckets.
- Alterar configurações.
- Acessar outros serviços AWS.

A arquitetura de permissões ficará assim:

```text
                    AWS Account
                        │
                        ▼
                  IAM User
                dev-estagiario
                        │
                        ▼
              Developers-Group
                        │
                        ▼
             IAM Policy Customizada
        S3 ReadOnly Specific Bucket
                        │
                        ▼
                Amazon S3 Bucket
                 (somente leitura)
```

A ideia é simples:

O usuário recebe acesso através do grupo, e o grupo recebe uma política.

Essa é uma boa prática porque facilita a administração quando existem dezenas ou centenas de usuários.

---

# 3. Passo a Passo

---

# Passo 1: Criando o Usuário e o Grupo IAM

## Criando o IAM User

1. Acesse o Console AWS.

2. Pesquise por:

```
IAM
```

3. No menu lateral:

```
Users
    └── Create user
```

4. Configure:

```
Username:
dev-estagiario
```

5. Marque:

```
Provide user access to the AWS Management Console
```

Isso cria uma identidade que consegue autenticar pelo navegador.

---

## Tipo de Usuário

Selecione:

```
I want to create an IAM user
```

Defina uma senha personalizada.

> Em ambientes reais, a AWS recomenda processos mais seguros, como Identity Center, Federation ou geração automática de credenciais temporárias.

Neste laboratório vamos manter simples para entender o conceito.

---

## Criando o Grupo

Na etapa de permissões:

Escolha:

```
Add user to group
```

Clique em:

```
Create group
```

Nome:

```
Developers-Group
```

Não associe nenhuma política neste momento.

Vamos criar uma política própria.

---

# Passo 2: Criando a IAM Policy de Menor Privilégio

Agora vamos criar a regra de autorização.

A autenticação responde:

> "Quem é você?"

A política responde:

> "O que você pode fazer?"

---

Acesse:

```
IAM
 └── Policies
      └── Create policy
```

Selecione a aba:

```
JSON
```

Cole:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucket",
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::nome-do-seu-bucket",
                "arn:aws:s3:::nome-do-seu-bucket/*"
            ]
        }
    ]
}
```

---

# Entendendo a "Sopa de Letrinhas" do IAM

Essa estrutura JSON aparece bastante nas provas.

Vamos desmontar:

---

## Version

```json
"Version": "2012-10-17"
```

Define a versão da linguagem de políticas IAM.

Na prática:

> Sempre utilize essa versão.

---

## Statement

```json
"Statement": []
```

Representa uma regra dentro da política.

Uma política pode possuir vários statements.

Exemplo:

- Permitir leitura do S3.
- Negar exclusão.
- Permitir acesso ao CloudWatch.

---

## Effect

```json
"Effect": "Allow"
```

Define o comportamento da regra.

Possíveis valores:

| Valor | Significado |
|---|---|
| Allow | Permitir acesso |
| Deny | Bloquear acesso |

---

## Action

```json
"Action": [
"s3:ListBucket",
"s3:GetObject"
]
```

Define quais operações podem ser executadas.

Neste caso:

| Permissão | Função |
|-|-|
| s3:ListBucket | Visualizar conteúdo do bucket |
| s3:GetObject | Ler/download de objetos |

Perceba que não existe:

```json
"s3:*"
```

Porque isso daria acesso total ao S3.

---

## Resource

```json
"Resource"
```

Define o alvo da permissão.

Temos dois recursos:

Bucket:

```
arn:aws:s3:::nome-do-seu-bucket
```

Objetos dentro dele:

```
arn:aws:s3:::nome-do-seu-bucket/*
```

O `/*` significa:

> Todos os arquivos dentro deste bucket.

---

# Salvando a Política

Clique em:

```
Next
```

Nome:

```
S3-ReadOnly-Specific-Bucket
```

Finalize a criação.

---

# Passo 3: Associando a Política ao Grupo

Agora vamos conectar tudo.

Fluxo:

```
IAM User
    │
    ▼
Developers-Group
    │
    ▼
IAM Policy
```

---

1. Acesse:

```
IAM
 └── User groups
```

2. Abra:

```
Developers-Group
```

3. Vá em:

```
Permissions
    └── Add permissions
          └── Attach policies
```

4. Procure:

```
S3-ReadOnly-Specific-Bucket
```

5. Anexe a política.

---

# Passo 4: Ativando MFA

Senha sozinha não é suficiente.

Se uma senha for vazada, o atacante possui acesso.

O MFA adiciona uma segunda camada:

```
Senha
 +
Código temporário
 =
Acesso autorizado
```

---

## Configuração

1. Faça login usando:

```
dev-estagiario
```

2. Clique no usuário no canto superior direito.

3. Entre em:

```
Security credentials
```

4. Localize:

```
Multi-factor authentication (MFA)
```

5. Clique:

```
Assign MFA device
```

6. Escolha:

```
Authenticator app
```

Exemplos:

- Google Authenticator
- Authy
- Microsoft Authenticator

7. Escaneie o QR Code.

8. Informe os dois códigos solicitados.

Pronto.

O usuário agora possui autenticação em duas etapas.

---

# 4. Validação: O Teste de Fogo

Agora vamos testar se nossa política realmente funciona.

---

## Teste 1: Acesso Permitido

Entre como:

```
dev-estagiario
```

Acesse:

```
Amazon S3
```

Abra o bucket configurado na política.

Resultado esperado:

✅ Usuário consegue listar arquivos.

✅ Usuário consegue baixar objetos.

---

## Teste 2: Acesso Bloqueado

Agora tente:

- Abrir outro bucket.
- Acessar EC2.
- Criar recursos.
- Excluir objetos.

Resultado esperado:

```
Access Denied
```

E isso é uma coisa boa.

Significa que a política está funcionando.

---

# 5. O Que Aprendemos Neste Lab

| Conceito | O que aprendemos |
|-|-|
| IAM User | Identidade utilizada para autenticação |
| IAM Group | Forma organizada de aplicar permissões |
| IAM Policy | Documento JSON que define permissões |
| Least Privilege | Dar somente o acesso necessário |
| MFA | Segunda camada de proteção |
| ARN | Identificador único dos recursos AWS |
| Access Denied | Indicação de bloqueio correto |

---

# 🎯 Gatilhos de Exame CLF-C02

Algumas associações que a prova gosta de cobrar:

---

## IAM Policy Visual Editor

Permite criar políticas sem escrever JSON manualmente.

Porém:

> A prova espera que você saiba interpretar o JSON.

---

## Attach Policy to Group

Melhor prática:

```
Usuário
   ↓
Grupo
   ↓
Política
```

Evite:

```
Usuário
   ↓
Permissão direta
```

porque dificulta gerenciamento em escala.

---

## Virtual MFA Device

É a opção mais comum e barata.

Normalmente utiliza aplicativos autenticadores.

---

## Access Denied

Quando aparece:

```
Access Denied
```

nem sempre significa erro.

Pode significar:

> A política de segurança está funcionando corretamente.

---

## Least Privilege

Sempre prefira:

```
s3:GetObject
s3:ListBucket
```

ao invés de:

```
s3:*
```

Menos permissões = menor superfície de ataque.

---

# ⚠️ Sinal de Alerta de Prova

Se a questão perguntar:

> Qual a forma mais segura de permitir que uma aplicação ou terceiro acesse recursos AWS?

A resposta geralmente será:

```
IAM Role
```

Porque utiliza:

- Credenciais temporárias.
- Rotação automática.
- Não exige armazenar Access Keys fixas.

Usuários IAM com chaves permanentes devem ser evitados quando existe uma alternativa melhor.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 2: Mnemonico - Watch vs Trail vs Config](12-mnemonico-watch-trail-config.md)
* [➡️ Módulo 2: Micro Simulado de Segurança](14-micro-simulado-seguranca.md)

---
---