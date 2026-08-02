# Amazon EC2: Instâncias Virtuais na Prática

Se você quer entender a AWS, tem que começar pelo **Amazon EC2 (Elastic Compute Cloud)**. Ele é um dos serviços mais importantes da plataforma e permite criar servidores virtuais (**instâncias**) sob demanda.

Em vez de comprar servidores físicos, investir em infraestrutura e se preocupar com manutenção (**CapEx**), você simplesmente provisiona uma instância em poucos minutos e paga apenas pelo tempo de uso (**OpEx**).

Essa flexibilidade é justamente um dos pilares da computação em nuvem: criar, redimensionar e remover servidores sempre que necessário.

---

## 1. Anatomia de uma Instância EC2

Criar uma instância EC2 vai muito além de clicar em **Launch Instance**. Existem alguns componentes fundamentais que definem como esse servidor será criado e como ele irá funcionar.

### AMI (Amazon Machine Image)

A **AMI** é o modelo utilizado para criar uma instância.

Ela funciona como uma imagem pronta contendo o sistema operacional e, opcionalmente, aplicações e configurações já instaladas.

Você pode utilizar:

- AMIs oficiais da AWS
- AMIs disponibilizadas pela comunidade
- AMIs do AWS Marketplace
- AMIs personalizadas criadas pela própria empresa

Utilizar AMIs padronizadas garante que todas as instâncias nasçam exatamente com a mesma configuração.

---

### Instance Types

Depois da AMI, você escolhe o hardware da máquina.

A AWS organiza as instâncias em famílias, cada uma otimizada para um tipo de carga de trabalho.

| Família | Melhor utilização |
|----------|------------------|
| **General Purpose (T, M)** | Equilíbrio entre CPU, memória e rede |
| **Compute Optimized (C)** | Processamento intenso, HPC e aplicações CPU-bound |
| **Memory Optimized (R, X)** | Bancos de dados e aplicações que consomem muita memória |
| **Storage Optimized (I, D, H)** | Alto desempenho de leitura e gravação em disco |

Na prova normalmente basta saber **qual família escolher para determinado cenário**, não decorar todos os modelos.

---

### Key Pairs

As **Key Pairs** funcionam como a identidade da instância.

Quando a máquina é criada:

- a AWS armazena a **chave pública**;
- você faz download da **chave privada** (`.pem` ou `.ppk`).

Ela será utilizada para acessar a instância:

- Linux → SSH
- Windows → RDP (para descriptografar a senha inicial)

> **Importante:** se você perder a chave privada, não existe botão de "recuperar senha". Será necessário utilizar outras técnicas para recuperar o acesso.

---

### Security Groups

Os **Security Groups** funcionam como um firewall virtual associado à instância.

Eles controlam quais conexões podem entrar e sair do servidor.

Uma característica muito cobrada na prova é que eles são **Stateful**.

Isso significa que, se uma conexão de entrada for permitida, a resposta será liberada automaticamente, sem necessidade de criar uma regra de saída correspondente.

Exemplo:

- Entrada TCP 80 liberada
- Cliente acessa o servidor
- A resposta HTTP retorna automaticamente

Não é necessário liberar a porta de saída manualmente.

---

### EBS (Elastic Block Store)

O **Amazon EBS** fornece armazenamento em bloco para as instâncias EC2.

Na prática, ele funciona como o "HD" do servidor.

Uma grande vantagem é que o volume é independente da instância.

Isso significa que, dependendo da configuração utilizada, você pode remover uma instância e reutilizar o mesmo volume em outra máquina, preservando os dados.

---

## 2. Automação com User Data

Criar um servidor e instalar tudo manualmente toda vez não faz sentido.

Para automatizar essa etapa existe o **User Data**.

O User Data permite executar scripts automaticamente durante o primeiro boot da instância.

Esses scripts podem:

- instalar pacotes;
- atualizar o sistema;
- instalar Docker;
- instalar Apache ou Nginx;
- baixar aplicações;
- alterar configurações;
- iniciar serviços.

Esse processo é conhecido como **Bootstrapping**, ou seja, a instância já nasce pronta para uso.

---

### Fluxo Simplificado

~~~mermaid
flowchart LR

    A["Seleciona AMI"]
    B["Define User Data"]
    C["Primeiro Boot"]
    D["Executa Script"]
    E["Servidor Configurado"]

    A --> B
    B --> C
    C --> D
    D --> E
~~~

---

## 3. Componentes de uma Instância EC2

Uma forma simples de visualizar tudo que participa da criação de uma instância é pensar neste fluxo:

~~~mermaid
flowchart TD

    EC2["🖥️ Amazon EC2"]

    EC2 --> AMI["AMI"]
    EC2 --> TYPE["Instance Type"]
    EC2 --> KEY["Key Pair"]
    EC2 --> SG["Security Group"]
    EC2 --> EBS["EBS Volume"]
    EC2 --> UD["User Data"]
~~~

---

## 4. Casos Clássicos de Prova

### Cenário 1

> Preciso criar vários servidores exatamente iguais.

Resposta: **AMI**

---

### Cenário 2

> Quero instalar automaticamente o Apache quando a máquina iniciar.

Resposta: **User Data**

---

### Cenário 3

> Preciso controlar quais portas podem acessar a instância.

Resposta: **Security Group**

---

### Cenário 4

> Quero alterar CPU e memória da máquina.

Resposta: **Instance Type**

---

### Cenário 5

> Preciso armazenar os dados do servidor em um disco persistente.

Resposta: **Amazon EBS**

---

## EC2 x Componentes

| Componente | Função |
|------------|---------|
| AMI | Modelo da instância |
| Instance Type | CPU, memória e rede |
| Security Group | Firewall Stateful |
| Key Pair | Autenticação SSH/RDP |
| User Data | Bootstrapping |
| EBS | Disco persistente |

---

## O que costuma cair na prova?

A CLF-C02 costuma cobrar principalmente:

- diferença entre AMI e Instance Type;
- função do User Data;
- Security Groups são **Stateful**;
- EBS fornece armazenamento persistente;
- EC2 é um serviço de computação.

---

## 🎯 Gatilho de Exame

Se aparecer...

| Enunciado | Resposta |
|------------|----------|
| Virtual Servers | Amazon EC2 |
| Compute Capacity | Amazon EC2 |
| AMI | Template da instância |
| Instance Type | Hardware da VM |
| User Data | Bootstrapping |
| Security Group | Firewall Stateful |
| EBS | Disco persistente |

---

## Pegadinhas da Prova

| Se a questão perguntar... | Resposta |
|---------------------------|----------|
| Firewall da instância | Security Group |
| Firewall da sub-rede | Network ACL |
| Script executado no primeiro boot | User Data |
| Template da máquina | AMI |
| Hardware da instância | Instance Type |
| Disco persistente | Amazon EBS |

---

> **💡 Dica de Ouro:** Pense na criação de uma instância como montar um computador. A **AMI** é a imagem do sistema operacional, o **Instance Type** é o hardware, o **EBS** é o HD, o **Security Group** é o firewall, a **Key Pair** é a chave de acesso e o **User Data** instala tudo automaticamente no primeiro boot.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 2: Micro Simulado de Segurança](../02-seguranca-identidade-e-conformidade/14-micro-simulado-seguranca.md)
* [➡️ Módulo 3: Opções de Compra EC2 e a Regra de Ouro Spot](01-opcoes-de-compra-regra-de-ouro-spot.md)

---
---