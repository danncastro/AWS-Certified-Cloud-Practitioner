# Amazon EMR: Processamento de Big Data com Hadoop e Spark

Processar terabytes ou petabytes de dados pode exigir uma quantidade absurda de computação.

Montar manualmente um cluster, instalar frameworks, configurar máquinas, distribuir o processamento e depois desmontar tudo?

**Dá trabalho pra caramba.**

É aí que entra o **Amazon EMR (Elastic MapReduce)**.

O EMR é um serviço gerenciado para executar **frameworks de Big Data** em clusters distribuídos na AWS.

Em vez de você passar dias montando a infraestrutura, o EMR ajuda a provisionar e configurar os recursos necessários para executar frameworks como **Apache Hadoop** e **Apache Spark**.

A ideia central é:

> **Você fornece o processamento e os dados. O EMR ajuda a montar e gerenciar o ambiente distribuído necessário para processá-los.**

---

## 1. O "Dream Team" do Big Data

O EMR não é simplesmente um "banco de dados gigante".

Ele fornece um ambiente gerenciado para executar diversos frameworks e ferramentas **open-source** de processamento e análise de Big Data.

Os nomes abaixo são importantes para reconhecer na prova:

| Framework / Ferramenta | Para que serve |
|---|---|
| **Apache Hadoop** | Ecossistema de Big Data para armazenamento e processamento distribuído |
| **Apache Spark** | Processamento distribuído de dados, com forte uso de memória |
| **Apache Hive** | Consultas e análise de grandes volumes usando uma linguagem semelhante a SQL |
| **Presto** | Motor de consultas SQL distribuído para análises interativas |
| **HBase** | Banco NoSQL distribuído baseado no ecossistema Hadoop |

### 🐘 Apache Hadoop

O Hadoop é um dos grandes pilares do ecossistema de Big Data.

Ele fornece componentes para trabalhar com grandes volumes de dados de forma distribuída.

Um dos conceitos associados ao Hadoop é o **MapReduce**, que divide o processamento em etapas que podem ser executadas em paralelo.

---

### ⚡ Apache Spark

O Spark é um framework de processamento distribuído conhecido por sua capacidade de realizar operações de análise e transformação de dados em larga escala.

Ele é muito utilizado quando precisamos processar grandes conjuntos de dados de forma paralela.

> **Gatilho de prova:**  
> Se o enunciado mencionar **EMR + Hadoop ou Spark**, pense imediatamente em **Big Data distribuído**.

---

### 🐝 Apache Hive

O Hive permite consultar e analisar grandes volumes de dados utilizando uma linguagem semelhante ao SQL.

Isso facilita a vida de quem já conhece SQL, mas precisa trabalhar com datasets enormes distribuídos em um ambiente de Big Data.

---

### 🔎 Presto

O Presto é um mecanismo de consultas SQL distribuídas.

Ele é utilizado para executar consultas analíticas sobre grandes volumes de dados de forma distribuída.

---

### 🗄️ HBase

O HBase é um banco de dados NoSQL distribuído associado ao ecossistema Hadoop.

Ele é adequado para cenários que exigem acesso rápido e aleatório a grandes volumes de dados estruturados em tabelas distribuídas.

---

## 2. Como o EMR processa tantos dados?

A resposta está em uma palavra:

**Distribuição.**

Em vez de uma única máquina tentar processar tudo:

~~~mermaid
flowchart LR

    DATA["💾 10 TB"]
        --> SERVER["🖥️ Servidor Único"]
        --> SLOW["🐢 Processamento demorado"]

    classDef data fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef server fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef slow fill:#FDECEA,stroke:#D32F2F,stroke-width:2px;

    class DATA data;
    class SERVER server;
    class SLOW slow;
~~~

O EMR pode distribuir o trabalho entre vários nós:

~~~mermaid
flowchart LR

    DATA["💾 10 TB"]

    DATA --> N1["🖥️ Node 1<br/>3.3 TB"]
    DATA --> N2["🖥️ Node 2<br/>3.3 TB"]
    DATA --> N3["🖥️ Node 3<br/>3.3 TB"]

    N1 --> RESULT["📊 Resultado"]
    N2 --> RESULT
    N3 --> RESULT

    classDef data fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef node fill:#F3E5F5,stroke:#8E24AA,stroke-width:2px;
    classDef result fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;

    class DATA data;
    class N1,N2,N3 node;
    class RESULT result;
~~~

Cada nó processa uma parte dos dados.

Isso permite executar workloads de **Big Data em paralelo**, aumentando a capacidade de processamento.

---

## 3. Desacoplamento de Computação e Armazenamento

Esse é um conceito importante para entender a arquitetura moderna do EMR.

Em um modelo tradicional, os dados e o processamento poderiam ficar fortemente ligados aos discos das máquinas do cluster.

Na AWS, podemos utilizar o **Amazon S3** como camada de armazenamento.

Isso permite separar:

- **Armazenamento:** Amazon S3
- **Processamento:** Amazon EMR

Imagine este fluxo:

~~~mermaid
flowchart LR

    S3["🪣 Amazon S3<br/><br/>Dados brutos<br/>Resultados"]
        --> EMR["⚙️ Amazon EMR<br/><br/>Processamento<br/>Hadoop / Spark"]

    classDef storage fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef processing fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;

    class S3 storage;
    class EMR processing;
~~~

O grande benefício é que o cluster de processamento não precisa ficar ligado o tempo inteiro.

### 💰 Exemplo prático

Imagine que você precisa processar 20 TB de logs uma vez por dia.

Você pode:

1. manter os dados no S3;
2. iniciar um cluster EMR;
3. executar o processamento;
4. gravar os resultados no S3;
5. encerrar o cluster.

O armazenamento continua no S3.

O ambiente de computação pode ser encerrado quando não estiver mais sendo necessário.

> **Papo de Arquiteto:** separar armazenamento de computação permite que você escale o processamento conforme a necessidade, sem precisar manter um cluster gigante funcionando 24/7.

---

## 4. Elasticidade e Escalabilidade

O EMR permite ajustar o tamanho do cluster conforme a necessidade do workload.

Se a carga aumenta:

~~~mermaid
flowchart LR

    LOAD["📈 Carga aumenta"]
        --> NODES["🖥️ Mais nós"]
        --> CAPACITY["⚡ Mais capacidade de processamento"]

    classDef load fill:#FDECEA,stroke:#D32F2F,stroke-width:2px;
    classDef nodes fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef capacity fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;

    class LOAD load;
    class NODES nodes;
    class CAPACITY capacity;
~~~

Quando a carga diminui, podemos reduzir a quantidade de recursos utilizados.

Isso evita manter capacidade computacional excessiva quando ela não é necessária.

---

## 5. Spot Instances: Economizando no Big Data

Aqui temos outra associação importante para a CLF-C02.

Workloads de Big Data frequentemente podem ser:

- distribuídos;
- paralelizados;
- reiniciados;
- executados novamente;
- tolerantes à perda de determinados nós.

Isso torna o EMR um cenário interessante para utilizar **Amazon EC2 Spot Instances**.

As Spot Instances oferecem capacidade EC2 com desconto em relação ao preço sob demanda, mas podem ser interrompidas quando a AWS precisar recuperar essa capacidade.

Por isso, elas são mais adequadas para workloads que conseguem tolerar interrupções.

### 💰 Exemplo

Imagine um processamento que precisa de 50 nós temporariamente.

Em vez de utilizar somente instâncias sob demanda, você pode utilizar Spot Instances em determinados nós do cluster quando o workload permitir.

~~~mermaid
flowchart LR

    EMR["⚙️ EMR Cluster"]

    EMR --> OD1["🖥️ On-Demand"]
    EMR --> OD2["🖥️ On-Demand"]
    EMR --> SPOT["💰 Spot"]

    SPOT --> COST["📉 Menor custo"]
    SPOT --> INTERRUPT["⚠️ Possibilidade de interrupção"]

    classDef cluster fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef ondemand fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef spot fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;
    classDef info fill:#F3E5F5,stroke:#8E24AA,stroke-width:2px;

    class EMR cluster;
    class OD1,OD2 ondemand;
    class SPOT spot;
    class COST,INTERRUPT info;
~~~
> **Atenção:** Spot não significa "garantia de até 90% de economia". O desconto varia conforme a capacidade e o tipo de instância. Para a prova, memorize a ideia principal: **Spot = custo menor em troca da possibilidade de interrupção**.

---

## 6. Arquitetura do Cluster EMR

Para entender o cluster do EMR, é importante conhecer os papéis dos diferentes tipos de nós.

### 🧠 Primary Node

O **Primary Node** coordena o cluster.

Ele é responsável por gerenciar componentes que coordenam o processamento distribuído e acompanhar o estado do cluster.

Em materiais antigos, você pode encontrar o termo **Master Node**.

Hoje, a nomenclatura utilizada pela AWS é **Primary Node**.

---

### ⚙️ Core Nodes

Os **Core Nodes** participam do processamento e também podem fornecer armazenamento para o cluster, dependendo da configuração utilizada.

Eles são responsáveis por executar tarefas de processamento e hospedar dados quando o armazenamento do cluster está sendo utilizado.

---

### 🚀 Task Nodes

Os **Task Nodes** são utilizados exclusivamente para processamento.

Eles não armazenam dados do HDFS.

Isso os torna interessantes para adicionar capacidade computacional temporária ao cluster.

Por exemplo:

> "Preciso de mais poder de processamento durante algumas horas."

Você pode adicionar Task Nodes e removê-los quando o processamento terminar.

Esse tipo de nó também pode ser um bom candidato para **Spot Instances**, dependendo do workload.

---

## 7. Arquitetura Visual

~~~mermaid
flowchart LR

    S3["🪣 Amazon S3<br/>Data Lake"]

    subgraph EMR["⚙️ Amazon EMR Managed Cluster"]

        P["👑 Primary Node<br/>Coordenador"]

        C1["🖥️ Core Node 1<br/>Processamento + Storage"]
        C2["🖥️ Core Node 2<br/>Processamento + Storage"]

        T1["⚡ Task Node 1<br/>Apenas Processamento"]
        T2["⚡ Task Node 2<br/>Apenas Processamento"]

        P --> C1
        P --> C2
        P -.-> T1
        P -.-> T2

    end

    S3 <--> P

    classDef storage fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef primary fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef core fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;
    classDef task fill:#F3E5F5,stroke:#8E24AA,stroke-width:2px;

    class S3 storage;
    class P primary;
    class C1,C2 core;
    class T1,T2 task;
~~~

O modelo mental é:

~~~mermaid
flowchart LR

    P["👑 Primary Node<br/>Coordenador"]

    P --> C1["🖥️ Core 1<br/>Processamento + Storage"]
    P --> C2["🖥️ Core 2<br/>Processamento + Storage"]
    P --> T["⚡ Task Nodes<br/>Apenas Processamento"]

    classDef primary fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef core fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;
    classDef task fill:#F3E5F5,stroke:#8E24AA,stroke-width:2px;

    class P primary;
    class C1,C2 core;
    class T task;
~~~

### 🧠 Memorize assim

**Primary → coordena**

**Core → processa + pode armazenar**

**Task → processa**

Essa associação é muito mais útil para a prova do que decorar uma lista gigante de componentes internos.

---

## 8. Quando usar o Amazon EMR?

Agora vamos transformar isso em cenários de prova.

### 📊 Big Data Processing

Use EMR quando precisar processar grandes volumes de dados utilizando frameworks distribuídos como Hadoop ou Spark.

Exemplo:

> "A empresa precisa processar vários terabytes de logs diariamente usando Apache Spark."

👉 **Amazon EMR**

---

### 🔄 Processamento distribuído

Quando o workload pode ser dividido entre vários nós e executado em paralelo, o EMR pode ser uma excelente opção.

Exemplo:

> "Dividir um dataset gigantesco entre dezenas de nós para executar transformações simultaneamente."

👉 **EMR**

---

### 🧪 Processamento temporário

Se você precisa de muito poder computacional apenas durante algumas horas, pode criar o cluster, executar o processamento e depois encerrá-lo.

Os dados podem continuar armazenados no S3.

---

### 💰 Big Data com foco em custo

Se o workload tolera interrupções, utilizar **Spot Instances** em partes do cluster pode reduzir significativamente o custo de computação.

---

## 🎯 Gatilho de Exame

Identifique o **Amazon EMR** por estas palavras-chave:

- **Amazon EMR:** plataforma gerenciada para executar frameworks de Big Data.
- **Big Data processing:** processamento de grandes volumes de dados.
- **Apache Hadoop:** framework clássico de Big Data.
- **Apache Spark:** processamento distribuído de dados.
- **Distributed data processing:** trabalho dividido entre vários nós.
- **Managed cluster:** AWS ajuda a provisionar e gerenciar o ambiente de processamento.
- **Petabyte-scale:** workloads envolvendo volumes gigantescos de dados.
- **Amazon S3:** armazenamento persistente separado da computação.
- **Spot Instances:** redução de custos em workloads tolerantes a interrupções.
- **Primary Node:** coordenação do cluster.
- **Core Nodes:** processamento e armazenamento do cluster.
- **Task Nodes:** capacidade adicional de processamento sem armazenamento HDFS.

---

## 🆚 EMR vs. Athena

Essa comparação é uma das mais importantes deste capítulo.

Os dois podem trabalhar com dados no S3, mas o objetivo é completamente diferente.

| Cenário | Serviço |
|---|---|
| Consultar arquivos no S3 usando SQL | **Athena** |
| Consulta SQL ad-hoc | **Athena** |
| Não quer administrar cluster | **Athena** |
| Processamento pesado de Big Data | **EMR** |
| Apache Spark | **EMR** |
| Apache Hadoop | **EMR** |
| Jobs distribuídos de transformação | **EMR** |
| Cluster de processamento customizável | **EMR** |

### 🧠 Regra mental

**S3 + SQL + consulta pontual → Athena**

**S3 + Hadoop/Spark + processamento pesado → EMR**

Não deixe o fato de ambos trabalharem com dados no S3 te confundir.

O que importa é **o que você quer fazer com esses dados**.

---

## 🚨 Sinal de Alerta

Se a questão disser:

> "A empresa possui arquivos no S3 e deseja executar consultas SQL ocasionais sem administrar servidores."

👉 **Amazon Athena**

Se disser:

> "A empresa precisa processar grandes volumes de dados utilizando Apache Spark ou Hadoop."

👉 **Amazon EMR**

Se disser:

> "O workload de Big Data pode tolerar interrupções e a empresa quer reduzir o custo de computação."

👉 **EMR + Spot Instances**

Se disser:

> "Os dados precisam permanecer armazenados de forma durável no S3, enquanto o cluster de processamento pode ser criado e encerrado conforme a necessidade."

👉 **EMR + S3**

### 🧠 Mantra para a prova

**Hadoop → EMR**

**Spark → EMR**

**Big Data distribuído → EMR**

**S3 + SQL → Athena**

**Spot + Big Data tolerante a interrupções → EMR**

E lembra:

> **Athena pergunta aos dados. EMR trabalha pesado em cima dos dados.**

Essa diferença salva questão.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 5: Amazon ElastiCache - Cache em Memória e o Motor Redis](05-cache-em-memoria-elasticache-redis.md)
* [➡️ Módulo 5: Amazon QuickSight - BI na Velocidade da Nuvem](07-visualizacao-de-dados-quicksight.md)

---
---