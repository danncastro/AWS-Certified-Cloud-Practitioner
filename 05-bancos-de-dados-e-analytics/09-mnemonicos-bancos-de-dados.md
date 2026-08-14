# Mnemônicos e Regras de Ouro: Bancos de Dados e Analytics

O Módulo 05 é um dos corações da prova CLF-C02.

A banca vai tentar te cansar colocando serviços com funções parecidas no mesmo cenário. O segredo é identificar o **verbo da operação** e o requisito principal do enunciado.

Se você aprender a associar **palavra-chave → serviço → cenário**, economiza minutos preciosos na prova.

Aqui está seu guia de bolso para não confundir S3 com Athena, RDS com Redshift ou ElastiCache com DAX.

---

## 1. Guia de Associação Rápida (Mnemônicos)

| Serviço | Palavra-Gatilho (Inglês) | Mnemônico / Frase de Fixação |
| :--- | :--- | :--- |
| **Amazon RDS** | *Relational / SQL / OLTP* | **RDS = Relacional Direto ao SQL.** Banco relacional gerenciado para aplicações que precisam de SQL e transações. |
| **Amazon Aurora** | *High performance / 6 copies / 3 AZs* | **Aurora = AURA de Poder.** Banco relacional compatível com MySQL e PostgreSQL, otimizado para alta disponibilidade e desempenho. |
| **DynamoDB** | *NoSQL / Key-value / Single-digit millisecond* | **Dynamo = DINAMITE na Escala.** Banco NoSQL serverless, altamente escalável e com latência de milissegundos de um dígito. |
| **Redshift** | *Data Warehouse / OLAP / Analytics* | **Redshift = REDE Analítica.** Data warehouse para análises em grande escala, especialmente sobre grandes volumes de dados. |
| **Athena** | *SQL on S3 / Serverless / Ad-hoc* | **Athena = ATENÇÃO no S3.** Executa consultas SQL diretamente sobre dados armazenados no S3, sem gerenciar servidores. |
| **ElastiCache** | *In-memory / Cache / Reduce DB load* | **ElastiCache = ELÁSTICO na RAM.** Cache em memória para acelerar aplicações e reduzir a quantidade de consultas ao banco. |
| **Amazon EMR** | *Hadoop / Spark / Big Data* | **EMR = EXÉRCITO de Máquinas.** Plataforma gerenciada para processamento distribuído de grandes volumes de dados. |
| **QuickSight** | *BI / Dashboards / Visualization* | **QuickSight = Olhar RÁPIDO.** Serviço de BI para criar dashboards e visualizações interativas. |
| **DocumentDB** | *MongoDB compatibility / Document database* | **DocumentDB = Documentos + MongoDB.** Banco de documentos compatível com workloads que usam MongoDB. |
| **Neptune** | *Graph / Relationships / Connected data* | **Neptune = NÓS conectados.** Banco de grafos para dados em que os relacionamentos são tão importantes quanto os próprios dados. |

### Como pensar na prova

Não tente decorar apenas o nome do serviço.

Decore a **necessidade que ele resolve**:

- Precisa de **SQL + transações** → RDS ou Aurora.
- Precisa de **NoSQL + escala automática** → DynamoDB.
- Precisa de **análise pesada sobre grandes volumes** → Redshift.
- Precisa fazer **SQL diretamente em arquivos no S3** → Athena.
- Precisa de **cache em memória** → ElastiCache.
- Precisa de **processamento distribuído de Big Data** → EMR.
- Precisa de **dashboards de BI** → QuickSight.
- Precisa de **compatibilidade com MongoDB** → DocumentDB.
- Precisa analisar **relacionamentos entre entidades** → Neptune.

> **Macete:** primeiro identifique o problema. Depois procure o serviço. Fazer o contrário é pedir para cair no distrator.

---

## 2. Palavras-Armadilha (Cuidado com o Distrator!)

A banca adora colocar serviços diferentes no mesmo cenário para ver se você percebe a diferença.

### OLTP vs. OLAP

Essa é uma das distinções mais importantes do módulo.

| Conceito | Pense em... | Serviço típico |
| :--- | :--- | :--- |
| **OLTP** | Transações do dia a dia | RDS / Aurora |
| **OLAP** | Análise e relatórios | Redshift |

**OLTP** é o mundo das operações:

- Registrar uma venda.
- Criar um cliente.
- Atualizar um pedido.
- Consultar o saldo de uma conta.
- Processar transações de um ERP ou CRM.

**OLAP** é o mundo da análise:

- Comparar vendas dos últimos 5 anos.
- Gerar relatórios corporativos.
- Analisar milhões ou bilhões de registros.
- Identificar tendências.
- Alimentar dashboards analíticos.

> **Pegadinha clássica:** "banco relacional" não significa automaticamente RDS. Se o objetivo principal é **analytics em larga escala**, pense em Redshift.

---

### Athena vs. Redshift

Os dois trabalham com SQL e analytics, mas o cenário é diferente.

**Athena**

Use quando o dado já está no **Amazon S3** e você quer executar consultas SQL diretamente sobre esses arquivos.

Exemplo:

> "A empresa possui arquivos Parquet no S3 e precisa executar consultas SQL ad-hoc sem provisionar servidores."

→ **Amazon Athena**

**Redshift**

Use quando a empresa precisa de um **data warehouse** para workloads analíticos mais estruturados e recorrentes.

Exemplo:

> "A empresa precisa consolidar grandes volumes de dados em um data warehouse para análises e BI."

→ **Amazon Redshift**

### Grave assim

**Athena → consulta o que está no S3.**

**Redshift → data warehouse para analytics.**

> Essa diferença aparece bastante em questões da CLF-C02.

---

### ElastiCache vs. DAX

Aqui a palavra-chave é **quem está sendo acelerado**.

**ElastiCache**

É um cache em memória de uso geral.

Pode ser usado para:

- Reduzir consultas ao RDS.
- Armazenar resultados frequentemente acessados.
- Melhorar a latência de uma aplicação.
- Aliviar a carga do banco de dados.

**DAX**

É específico para **DynamoDB**.

Ele funciona como uma camada de cache gerenciada para acelerar leituras do DynamoDB.

### Macete

**Cache genérico → ElastiCache**

**Cache específico do DynamoDB → DAX**

> Se o enunciado falar explicitamente em **DynamoDB + cache**, acenda a luz do DAX.

---

### NoSQL vs. Relacional

Aqui não complique.

Se o cenário fala em:

- SQL.
- Relacionamentos entre tabelas.
- Joins.
- Integridade referencial.
- Transações relacionais.

→ **RDS / Aurora**

Se fala em:

- NoSQL.
- Chave-valor.
- Documentos.
- Esquema flexível.
- Escala horizontal.
- Alta taxa de requisições.

→ **DynamoDB**

Um detalhe importante para a prova:

O DynamoDB oferece latência de **milissegundos de um dígito**, não "microssegundos" por padrão.

Microssegundos é uma pista muito mais forte para uma solução de **cache em memória**, como ElastiCache ou DAX.

---

## 🎯 Gatilho de Exame

Agora vem a parte para revisão rápida.

Se você bater o olho no enunciado e encontrar estas expressões, pense imediatamente:

### 1. "SQL queries directly on Amazon S3"

→ **Amazon Athena**

O Athena é serverless e permite consultar dados armazenados no S3 usando SQL.

**Palavra-chave:** SQL + S3.

---

### 2. "Apache Hadoop or Apache Spark"

→ **Amazon EMR**

O EMR é usado para executar frameworks de Big Data, como Hadoop e Spark, em ambientes distribuídos.

**Palavra-chave:** Hadoop / Spark / Big Data.

---

### 3. "In-memory cache" ou "reduce database load"

→ **Amazon ElastiCache**

A ideia é manter dados frequentemente acessados em memória para reduzir a necessidade de consultar o banco principal.

**Palavra-chave:** cache + memória + acelerar aplicação.

---

### 4. "6 copies of data across 3 Availability Zones"

→ **Amazon Aurora**

A arquitetura de armazenamento do Aurora mantém múltiplas cópias dos dados distribuídas entre Availability Zones.

**Palavra-chave:** 6 cópias + 3 AZs.

> **Atenção:** não confunda isso com "seis instâncias". O conceito aqui está relacionado à camada de armazenamento distribuído do Aurora.

---

### 5. "BI dashboards" ou "data visualization"

→ **Amazon QuickSight**

O QuickSight é o serviço de Business Intelligence da AWS para criação de dashboards e visualizações.

**Palavra-chave:** dashboard + BI.

> **Cuidado:** características de preço do QuickSight podem mudar com o tempo. Para a prova, priorize entender o que o serviço faz em vez de decorar um modelo específico de cobrança.

---

### 6. "Document database" ou "MongoDB compatibility"

→ **Amazon DocumentDB**

Quando o cenário fala em banco de documentos e compatibilidade com workloads do MongoDB, pense em DocumentDB.

**Palavra-chave:** documentos + MongoDB.

---

### 7. "Graph database" ou "highly connected data"

→ **Amazon Neptune**

Se o problema envolve relacionamentos complexos entre entidades, como:

- Redes sociais.
- Recomendações.
- Grafos de conhecimento.
- Detecção de fraude baseada em relacionamentos.

→ **Neptune**

**Palavra-chave:** relacionamentos + grafo.

---

## 🧠 Mapa Mental de 30 Segundos

Se precisar revisar tudo antes da prova, pense nesta sequência:

| Se o enunciado falar em... | Pense em... |
| :--- | :--- |
| **SQL + transações** | RDS / Aurora |
| **NoSQL + chave-valor** | DynamoDB |
| **SQL + arquivos no S3** | Athena |
| **Data Warehouse + analytics** | Redshift |
| **Cache + memória** | ElastiCache |
| **DynamoDB + cache** | DAX |
| **Hadoop / Spark / Big Data** | EMR |
| **Dashboards / BI** | QuickSight |
| **Documentos / MongoDB** | DocumentDB |
| **Grafos / relacionamentos** | Neptune |

---

## 🚨 Sinal de Alerta

A prova pode tentar te fazer acreditar que o **Amazon S3 é um banco de dados**.

**Não é.**

O S3 é um serviço de **armazenamento de objetos**.

Você pode armazenar nele:

- Arquivos CSV.
- JSON.
- Parquet.
- Imagens.
- Logs.
- Backups.
- Datasets.

O **Athena** pode consultar esses dados usando SQL, mas isso não transforma o S3 em um banco de dados relacional.

Pense assim:

**S3 = onde os dados ficam.**

**Athena = ferramenta que consulta os dados do S3.**

**RDS / Aurora = banco relacional para aplicações transacionais.**

**DynamoDB = banco NoSQL altamente escalável.**

**Redshift = data warehouse para analytics.**

> **Essa é uma das pegadinhas favoritas:** o enunciado pode colocar "SQL + S3" e tentar te empurrar para RDS. Não caia. Se o SQL está sendo executado diretamente sobre arquivos no S3, o gatilho é **Athena**.

**Papo reto:** não decore os serviços como uma lista. Decore o **problema que cada um resolve**. Na hora da prova, o enunciado muda as palavras, mas o problema continua sendo o mesmo.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 5: RDS vs. DynamoDB - O Duelo de Titãs dos Bancos de Dados](08-tabela-rds-vs-dynamodb-relacional-vs-nosql.md)
* [➡️ Módulo 5: Lab - Alta Disponibilidade com RDS Multi-AZ](10-lab-criando-banco-rds-multi-az.md)

---
---