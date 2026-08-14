# Amazon Athena: Consultas SQL no S3 sem Servidores

Imagine que você tem gigabytes ou terabytes de logs e arquivos armazenados em um bucket do **Amazon S3** e alguém chega com aquela clássica:

> "Preciso de um relatório sobre esses dados. Pra ontem."

Você precisa subir um RDS? Criar servidores? Montar um banco inteiro? Fazer ETL antes de conseguir descobrir alguma coisa?

**Não necessariamente.**

É aí que entra o **Amazon Athena**.

O Athena permite executar **consultas SQL diretamente sobre dados armazenados no S3**, sem precisar carregar esses arquivos para um banco de dados tradicional.

Você mantém os dados no S3 e utiliza o Athena como o mecanismo de consulta.

> **Pense assim:**  
> **S3 = onde os dados estão.**  
> **Athena = quem vai até eles e faz as perguntas usando SQL.**

E o melhor: você não precisa administrar servidores ou clusters para fazer isso.

---

## 1. O que é o Amazon Athena?

O **Amazon Athena** é um serviço **Serverless de consultas interativas**.

Você aponta o Athena para os dados armazenados no S3, define como esses dados devem ser interpretados e executa suas consultas SQL.

A infraestrutura necessária para processar as consultas é gerenciada pela AWS.

Você se preocupa com:

- os dados;
- a estrutura lógica dos dados;
- a consulta SQL.

A AWS se preocupa com a infraestrutura necessária para executar a consulta.

### Principais Características

### ☁️ Serverless

Não existe cluster de banco de dados para você ficar administrando.

Você não precisa:

- provisionar EC2;
- escolher CPU e memória;
- instalar banco;
- aplicar patches;
- gerenciar servidores;
- manter um cluster de consulta.

Você simplesmente executa a consulta.

> **Pegadinha:** Serverless não significa que o Athena "não usa servidores". Significa que **você não precisa gerenciar a infraestrutura que executa o serviço**.

---

### 🪣 Integração direta com S3

O Athena foi projetado para consultar dados que estão no **Amazon S3**.

Imagine um Data Lake:

~~~text
Amazon S3
│
├── logs/
├── vendas/
├── clientes/
├── eventos/
└── métricas/
~~~

Esses arquivos continuam no S3.

O Athena lê os dados necessários para executar a consulta e retorna o resultado.

Você não precisa transformar o S3 em um banco relacional antes de começar a analisar os dados.

Por isso, o Athena é muito útil quando a empresa já possui um **Data Lake no S3** e precisa explorar esses dados usando SQL.

---

### 👓 Schema-on-Read

Essa expressão parece complicada, mas a ideia é simples.

No modelo tradicional de banco de dados, normalmente você define a estrutura da tabela e depois insere os dados seguindo aquele esquema.

No Athena, os dados podem permanecer armazenados como arquivos no S3.

O esquema é aplicado **quando os dados são lidos**.

Pense em uma lente:

~~~mermaid
flowchart TD

    S3["🪣 Arquivos no Amazon S3"]
        --> SCHEMA["📐 Schema"]

    SCHEMA --> ATHENA["🔎 Amazon Athena"]

    ATHENA --> SQL["🗃️ SQL Query"]

    SQL --> RESULT["📊 Resultado"]

    classDef storage fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef schema fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef athena fill:#F3E5F5,stroke:#8E24AA,stroke-width:2px;
    classDef query fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;
    classDef result fill:#E0F2F1,stroke:#00796B,stroke-width:2px;

    class S3 storage;
    class SCHEMA schema;
    class ATHENA athena;
    class SQL query;
    class RESULT result;
~~~

Os arquivos originais continuam no S3.

O Athena utiliza a definição da tabela para interpretar esses arquivos durante a consulta.

> **Schema-on-Read = o esquema é aplicado na leitura, e não necessariamente quando os dados são gravados.**

Essa característica é muito útil em **Data Lakes**, onde os dados podem chegar em diferentes momentos e formatos.

---

## 2. Modelo de Cobrança: Pay-per-query

Aqui está um ponto que merece atenção na prova.

O Athena não funciona como um servidor que você mantém ligado e paga por hora de máquina.

A cobrança é baseada principalmente na **quantidade de dados processados pelas consultas**.

Em termos simples:

> **Quanto mais dados sua consulta precisar processar, maior tende a ser o custo.**

Imagine:

~~~mermaid
flowchart LR

    subgraph A["🔎 Consulta A"]
        A1["📦 100 MB processados"]
        A2["💰 Custo menor"]

        A1 --> A2
    end

    subgraph B["🔎 Consulta B"]
        B1["📦 1 TB processado"]
        B2["💸 Custo maior"]

        B1 --> B2
    end

    classDef low fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;
    classDef high fill:#FDECEA,stroke:#D32F2F,stroke-width:2px;

    class A1,A2 low;
    class B1,B2 high;
~~~

Por isso, uma das grandes preocupações ao utilizar Athena é **evitar processar dados desnecessariamente**.

### 💰 Como reduzir o custo?

Aqui entra uma dica de arquitetura que também ajuda na performance.

Prefira formatos de dados eficientes para análise, principalmente:

- **Parquet:** formato colunar que permite ler somente as colunas necessárias.
- **ORC:** outro formato colunar otimizado para workloads analíticos.
- **Compressão:** reduz a quantidade de dados que precisa ser lida e transferida.

Por exemplo, imagine uma tabela com 100 colunas.

Sua consulta precisa de apenas:

~~~sql
SELECT customer_id, total
FROM sales;
~~~

Com um formato colunar adequado, o mecanismo pode evitar processar todas as outras colunas desnecessariamente.

Resultado:

- menos dados processados;
- consultas potencialmente mais rápidas;
- menor custo.

> **Papo de Arquiteto:** no Athena, **otimizar o armazenamento também pode significar otimizar a conta**.

---

## 3. Quando usar o Athena? (Casos de Uso)

O Athena não foi feito para substituir o banco transacional da sua aplicação.

Ele brilha quando você precisa fazer **análises pontuais, exploratórias ou interativas sobre dados armazenados no S3**.

### 🔎 Análise de Logs da AWS

Esse é um cenário clássico.

Imagine que você possui:

- **VPC Flow Logs:** investigar tráfego e problemas de rede.
- **CloudTrail Logs:** analisar atividades e chamadas de API.
- **S3 Access Logs:** investigar acessos aos objetos.
- **ELB Access Logs:** analisar requisições recebidas pelo Load Balancer.

Em vez de criar um banco apenas para armazenar esses logs e depois consultá-los, você pode armazená-los no S3 e utilizar o Athena para analisá-los com SQL.

> **Cenário clássico de prova:**  
> "A empresa possui logs armazenados no S3 e precisa realizar consultas SQL ocasionais sobre esses dados."
>
> 👉 **Amazon Athena**

---

### 📊 Relatórios rápidos

Você recebeu um conjunto de arquivos CSV ou JSON e precisa descobrir algumas informações rapidamente.

Por exemplo:

- quantas vendas existem por região;
- qual produto possui mais ocorrências;
- qual foi o faturamento por mês;
- quais registros possuem determinado valor.

Não necessariamente vale a pena montar um Data Warehouse inteiro para isso.

O Athena permite consultar os dados diretamente no S3.

---

### 🧪 Exploração de Data Lake

O Athena também é útil para explorar dados que já estão armazenados em um **Data Lake no S3**.

Por exemplo:

> "Antes de carregar esses dados para uma plataforma analítica, quero descobrir se os arquivos possuem a estrutura e a qualidade esperadas."

Você pode utilizar SQL para investigar os dados sem precisar primeiro transformá-los em um banco tradicional.

---

### 📁 Dados estruturados e semiestruturados

O Athena pode consultar diferentes formatos de dados armazenados no S3.

Entre os exemplos comuns estão:

- **CSV**
- **JSON**
- **Parquet**
- **ORC**

A escolha do formato pode impactar bastante o desempenho e o custo das consultas.

Para workloads analíticos, formatos colunares como **Parquet** e **ORC** costumam ser especialmente interessantes.

---

## 🆚 Athena vs. Redshift

Essa comparação é praticamente obrigatória para a CLF-C02.

Os dois podem aparecer em cenários de análise de dados, mas o contexto é diferente.

| Característica | Amazon Athena | Amazon Redshift |
|---|---|---|
| Tipo | Serviço de consulta Serverless | Data Warehouse |
| Dados | Consultados diretamente no S3 | Armazenados e gerenciados no ambiente do Data Warehouse |
| SQL | ✅ Sim | ✅ Sim |
| Infraestrutura para gerenciar | ❌ Não | Gerenciada pela AWS |
| Principal cenário | Consultas ad-hoc sobre dados no S3 | Analytics e BI em Data Warehouse |
| Data Lake no S3 | 🟢 Excelente opção | Pode integrar com dados do S3 |
| Workloads analíticos recorrentes | 🟢 Pode atender | 🟢 Excelente opção |
| Data Warehouse estruturado | ❌ Não é o foco | 🟢 Principal finalidade |

### Como diferenciar na prova?

**Dados já estão no S3 + quer consultar com SQL + não quer carregar os dados para um banco:**

👉 **Athena**

**Grande ambiente analítico + Data Warehouse + BI + consultas complexas recorrentes:**

👉 **Redshift**

> **Não caia na armadilha do "ambos usam SQL".**
>
> O que diferencia os dois é principalmente **onde estão os dados e qual é o objetivo da arquitetura**.

---

## 🆚 Athena vs. RDS

Agora outra comparação importante.

| Característica | Amazon Athena | Amazon RDS |
|---|---|---|
| Principal finalidade | Consultar dados no S3 | Banco de dados relacional |
| Modelo | Consulta sobre objetos no S3 | Banco relacional |
| OLTP | ❌ Não é o foco | 🟢 Sim |
| OLAP / Analytics | 🟢 Sim | 🟡 Pode fazer, mas não é o foco |
| Serverless | ✅ Sim | O RDS gerencia a infraestrutura de banco, mas não é equivalente ao modelo Serverless do Athena |
| Dados no S3 | 🟢 Consulta diretamente | Não é seu modelo principal |
| Transações da aplicação | ❌ Não | 🟢 Sim |

### Exemplo prático

Uma loja virtual precisa registrar:

> "Cliente 123 comprou 2 notebooks."

Isso é uma operação transacional.

👉 **RDS / Aurora**

Agora imagine:

> "Qual foi o faturamento total de todas as vendas realizadas nos últimos cinco anos?"

Isso é análise.

Se os dados estiverem armazenados no S3:

👉 **Athena**

Se a empresa precisar de um Data Warehouse dedicado para análises recorrentes e complexas:

👉 **Redshift**

---

## 🧠 Arquitetura Simplificada

O fluxo básico do Athena pode ser visualizado assim:

~~~mermaid
flowchart LR

    U["👨‍💻 Dev / Analista"]
        -->|"SQL Query"| A["🔎 Amazon Athena"]

    subgraph AWS["☁️ AWS — Serverless"]
        A
    end

    A -->|"Lê dados"| S3["🪣 Amazon S3<br/>Data Lake"]

    S3 -->|"Dados"| A

    A -->|"Resultado da consulta"| U

    classDef user fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef athena fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef storage fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;

    class U user;
    class A athena;
    class S3 storage;
~~~

A ideia central é:

~~~mermaid
flowchart LR

    SQL["🗃️ SQL Query"]
        --> ATHENA["🔎 Amazon Athena"]
        --> S3["🪣 Amazon S3"]
        --> DATA["📊 Dados"]

    classDef query fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef athena fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef storage fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;
    classDef data fill:#F3E5F5,stroke:#8E24AA,stroke-width:2px;

    class SQL query;
    class ATHENA athena;
    class S3 storage;
    class DATA data;
~~~

Você não precisa mover os dados para um banco apenas para executar uma análise pontual.

---

## 🎯 Gatilho de Exame

Identifique o **Amazon Athena** no enunciado por estas pistas:

- **Amazon Athena:** serviço Serverless para consultas interativas.
- **Serverless query service:** não é necessário gerenciar servidores ou clusters de consulta.
- **Query data in Amazon S3 using SQL:** uma das pistas mais fortes para Athena.
- **Data stored in S3:** os dados já estão no Data Lake.
- **Pay-per-query:** cobrança associada à quantidade de dados processados.
- **Ad-hoc analytics:** análises pontuais e exploratórias.
- **Schema-on-Read:** o esquema é aplicado durante a leitura.
- **Structured and semi-structured data:** pode consultar formatos como CSV, JSON, Parquet e ORC.
- **Logs in S3:** cenário clássico para consultas usando Athena.

---

## 🚨 Sinal de Alerta

Se a questão disser:

> "A empresa possui arquivos armazenados no S3 e precisa executar consultas SQL ocasionais sem carregar os dados para um banco de dados."

👉 **Amazon Athena**

Se disser:

> "A empresa precisa de um Data Warehouse para executar análises complexas e recorrentes sobre grandes volumes de dados."

👉 **Amazon Redshift**

Se disser:

> "A aplicação precisa registrar transações de clientes em tempo real."

👉 **Amazon RDS / Aurora**

### 🧠 Mantra para a prova

**S3 + SQL + Serverless → Athena**

**Data Warehouse + Analytics + BI → Redshift**

**Banco relacional + Transações → RDS/Aurora**

E se aparecer **logs no S3 + consulta SQL + análise pontual**?

**Athena.**

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 5: Amazon Redshift - Data Warehousing e Analytics em Larga Escala](03-redshift-data-warehousing-analytics.md)
* [➡️ Módulo 5: Amazon ElastiCache - Cache em Memória e o Motor Redis](05-cache-em-memoria-elasticache-redis.md)

---
---