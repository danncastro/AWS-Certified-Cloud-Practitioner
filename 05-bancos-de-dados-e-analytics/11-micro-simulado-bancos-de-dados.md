# Micro-Simulado: Bancos de Dados e Analytics

Banco de dados é o coração de praticamente qualquer aplicação, e na CLF-C02 a AWS quer saber se você consegue escolher o serviço certo de acordo com o problema.

A banca pode misturar serviços parecidos no mesmo cenário para ver se você identifica o requisito principal. Não basta saber que "RDS é banco" ou que "S3 guarda dados".

Você precisa reconhecer **o tipo de workload**, **o modelo de dados** e **como os dados serão utilizados**.

Este micro-simulado foi feito justamente para treinar esses gatilhos.

Bora testar se você está afiado.

---

## Questões

### 1. Banco NoSQL para aplicações em alta escala

Uma empresa está desenvolvendo uma aplicação de comércio eletrônico que precisa armazenar informações de produtos, pedidos e sessões de usuários.

A aplicação deve suportar um grande volume de requisições sem que a equipe precise gerenciar servidores de banco de dados.

O modelo de dados pode utilizar estruturas de chave-valor e documentos, e a aplicação precisa de respostas em milissegundos de um dígito.

Qual serviço atende melhor a esse cenário?

A) Amazon RDS  
B) Amazon DynamoDB  
C) Amazon Redshift  
D) Amazon Athena  

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **<b>Resposta Correta: B (Amazon DynamoDB)</b>**
>
> * **<b>Por que é a certa:</b>** O Amazon DynamoDB é um banco de dados NoSQL totalmente gerenciado e serverless, projetado para aplicações que precisam de alta escala e baixa latência.
>
> * **<b>Os gatilhos:</b>** O cenário combina quatro pistas importantes: **NoSQL + chave-valor/documentos + serverless + single-digit millisecond latency**.
>
> * **<b>A) Amazon RDS:</b>** É voltado para bancos relacionais. Seria uma escolha natural se o cenário exigisse SQL, relacionamentos entre tabelas ou recursos tradicionais de bancos relacionais.
>
> * **<b>C) Amazon Redshift:</b>** É um Data Warehouse voltado para analytics e OLAP. O cenário descreve uma aplicação transacional, não um workload analítico.
>
> * **<b>D) Amazon Athena:</b>** Executa consultas SQL sobre dados armazenados no S3. Não é o banco operacional utilizado para armazenar os dados da aplicação.
>
> * **<b>A pegadinha:</b>** "Alta escala" não significa automaticamente Redshift. Primeiro identifique o tipo de workload. Aplicação transacional com baixa latência aponta para DynamoDB.

</details>

---

### 2. Banco relacional desenvolvido para a nuvem

Uma empresa está migrando uma aplicação que utiliza MySQL para a AWS.

A equipe deseja continuar utilizando um banco relacional compatível com MySQL, mas busca uma solução gerenciada, com alta performance e uma arquitetura de armazenamento distribuída entre múltiplas Availability Zones.

Qual serviço atende melhor a esse cenário?

A) Amazon RDS for MariaDB  
B) Amazon DocumentDB  
C) Amazon Aurora  
D) Amazon ElastiCache  

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **<b>Resposta Correta: C (Amazon Aurora)</b>**
>
> * **<b>Por que é a certa:</b>** O Amazon Aurora é um banco de dados relacional gerenciado e compatível com MySQL e PostgreSQL. Sua arquitetura de armazenamento distribuído mantém múltiplas cópias dos dados em diferentes Availability Zones, oferecendo alta disponibilidade e resiliência.
>
> * **<b>Os gatilhos:</b>** Procure pela combinação **relacional + MySQL/PostgreSQL + alta performance + armazenamento distribuído + múltiplas AZs**.
>
> * **<b>A) Amazon RDS for MariaDB:</b>** Também é um banco relacional gerenciado, mas o cenário destaca características de arquitetura e performance associadas ao Aurora.
>
> * **<b>B) Amazon DocumentDB:</b>** É um banco de documentos compatível com workloads do MongoDB. Não é um banco relacional.
>
> * **<b>D) Amazon ElastiCache:</b>** É utilizado para caching em memória. Pode complementar um banco de dados, mas não substituí-lo nesse cenário.
>
> * **<b>A pegadinha:</b>** Aurora continua sendo um banco **relacional**. A arquitetura distribuída não o transforma em NoSQL.

</details>

---

### 3. Consultando arquivos diretamente no S3

Uma empresa armazena vários terabytes de logs em arquivos CSV e JSON no Amazon S3.

Um analista precisa executar consultas SQL ocasionais para investigar esses dados. A equipe não quer provisionar servidores nem administrar uma infraestrutura de banco de dados apenas para essas consultas.

Qual serviço é o mais adequado?

A) Amazon Redshift  
B) Amazon EMR  
C) Amazon Athena  
D) Amazon RDS for PostgreSQL  

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **<b>Resposta Correta: C (Amazon Athena)</b>**
>
> * **<b>Por que é a certa:</b>** O Amazon Athena é um serviço de consultas serverless que permite executar SQL diretamente sobre dados armazenados no S3. É especialmente adequado para consultas ad-hoc sem necessidade de administrar servidores.
>
> * **<b>Os gatilhos:</b>** **SQL + S3 + consultas ad-hoc + serverless** praticamente gritam "Athena".
>
> * **<b>A) Amazon Redshift:</b>** É um Data Warehouse voltado para workloads analíticos. Pode trabalhar com dados no S3, mas o cenário pede uma solução simples e serverless para consultar diretamente os objetos.
>
> * **<b>B) Amazon EMR:</b>** É utilizado para processamento distribuído de Big Data com tecnologias como Apache Spark e Hadoop. Seria uma solução muito mais complexa para o problema apresentado.
>
> * **<b>D) Amazon RDS for PostgreSQL:</b>** É um banco relacional gerenciado. O cenário não pede um banco para armazenar os logs, mas uma forma de consultá-los diretamente no S3.
>
> * **<b>A pegadinha:</b>** Terabytes de dados não significa automaticamente Redshift ou EMR. O requisito principal é **consultar arquivos existentes no S3 usando SQL sem gerenciar servidores**.

</details>

---

### 4. Data Warehouse para Business Intelligence

Uma organização deseja centralizar grandes volumes de dados provenientes de sistemas de vendas, marketing e atendimento.

A equipe de BI precisa executar consultas analíticas complexas, gerar relatórios históricos e identificar tendências de negócio.

Qual serviço AWS é mais adequado para atuar como Data Warehouse?

A) Amazon DynamoDB  
B) Amazon ElastiCache  
C) Amazon Redshift  
D) Amazon Aurora  

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **<b>Resposta Correta: C (Amazon Redshift)</b>**
>
> * **<b>Por que é a certa:</b>** O Amazon Redshift é um Data Warehouse projetado para workloads analíticos. O cenário apresenta características típicas de **OLAP**: grandes volumes de dados, consultas analíticas, relatórios históricos e Business Intelligence.
>
> * **<b>A) Amazon DynamoDB:</b>** É voltado para workloads NoSQL de alta escala e baixa latência, principalmente aplicações transacionais. Não é a escolha principal para Data Warehouse.
>
> * **<b>B) Amazon ElastiCache:</b>** É uma camada de cache em memória. Serve para acelerar o acesso a dados, não para funcionar como Data Warehouse.
>
> * **<b>D) Amazon Aurora:</b>** É um banco relacional de alta performance adequado para workloads transacionais. O cenário, porém, está claramente focado em analytics e BI.
>
> * **<b>A pegadinha:</b>** Aurora e Redshift podem trabalhar com dados relacionais, mas resolvem problemas diferentes. **OLTP → Aurora/RDS. OLAP → Redshift.**

</details>

---

### 5. Cache em memória para reduzir carga no banco

Uma aplicação web consulta repetidamente os mesmos dados armazenados em um banco de dados relacional.

Durante períodos de alta demanda, o banco começa a receber muitas consultas repetitivas, aumentando a latência da aplicação.

A equipe deseja adicionar uma camada de cache em memória para reduzir a quantidade de consultas enviadas ao banco principal.

Qual serviço é mais adequado?

A) Amazon ElastiCache  
B) Amazon CloudFront  
C) Amazon DAX  
D) AWS Lambda  

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **<b>Resposta Correta: A (Amazon ElastiCache)</b>**
>
> * **<b>Por que é a certa:</b>** O Amazon ElastiCache fornece caching gerenciado em memória e pode ser utilizado para reduzir a carga sobre bancos de dados e melhorar a latência das aplicações.
>
> * **<b>A) Amazon CloudFront:</b>** É uma CDN utilizada para distribuir e armazenar conteúdo em cache próximo aos usuários. Não é uma solução para cache de consultas de banco de dados.
>
> * **<b>B) Amazon DAX:</b>** O DynamoDB Accelerator é uma solução de caching específica para o DynamoDB. Como o cenário utiliza um banco relacional, DAX não é adequado.
>
> * **<b>C) AWS Lambda:</b>** É um serviço de computação serverless. Pode executar código para acessar o banco, mas não é uma solução de caching.
>
> * **<b>A pegadinha:</b>** Não basta aparecer a palavra "cache". Descubra **o que está sendo acelerado**. Banco relacional ou aplicação geral → ElastiCache. DynamoDB → DAX.

</details>

---

## 🎯 Gatilho de Exame

Não tente decorar apenas o nome dos serviços. Procure primeiro pelo **problema que o enunciado está tentando resolver**.

- **SQL + aplicação transacional + banco relacional** → **Amazon RDS / Aurora**
- **Relacional + alta performance + arquitetura distribuída** → **Amazon Aurora**
- **NoSQL + chave-valor/documentos + alta escala** → **Amazon DynamoDB**
- **SQL diretamente sobre arquivos no S3 + serverless** → **Amazon Athena**
- **Data Warehouse + BI + analytics + OLAP** → **Amazon Redshift**
- **Cache em memória + reduzir carga do banco** → **Amazon ElastiCache**
- **Cache específico para DynamoDB** → **Amazon DAX**
- **Hadoop / Spark / processamento distribuído de Big Data** → **Amazon EMR**
- **Banco de documentos + compatibilidade com MongoDB** → **Amazon DocumentDB**
- **Banco de grafos + relacionamentos complexos** → **Amazon Neptune**

### 🧠 Atalho Mental

| Se o problema é... | Pense em... |
| :--- | :--- |
| **Transação** | RDS / Aurora / DynamoDB |
| **NoSQL** | DynamoDB |
| **SQL no S3** | Athena |
| **Analytics / OLAP** | Redshift |
| **Cache** | ElastiCache |
| **Cache do DynamoDB** | DAX |
| **Big Data distribuído** | EMR |
| **Documentos / MongoDB** | DocumentDB |
| **Grafos / relacionamentos** | Neptune |

---

> **🚨 Sinal de Alerta**
>
> A banca pode colocar vários serviços de dados no mesmo enunciado e tentar fazer você escolher pelo nome mais familiar.
>
> Não caia nessa.
>
> **Amazon RDS ≠ Amazon Redshift**
>
> - **RDS:** banco relacional para aplicações transacionais.
> - **Redshift:** Data Warehouse para analytics.
>
> **Athena ≠ Redshift**
>
> - **Athena:** SQL diretamente sobre dados no S3.
> - **Redshift:** Data Warehouse para workloads analíticos.
>
> **ElastiCache ≠ DAX**
>
> - **ElastiCache:** cache em memória de uso geral.
> - **DAX:** cache específico para DynamoDB.
>
> **S3 ≠ Banco de Dados**
>
> O Amazon S3 é armazenamento de objetos. Ele pode armazenar enormes volumes de dados, mas isso não o transforma em um banco de dados.
>
> Uma arquitetura pode combinar serviços diferentes:
>
> **S3 → armazena os dados**
>
> **Athena → consulta os dados**
>
> **Redshift → realiza analytics em um Data Warehouse**
>
> Cada serviço resolve um problema diferente.

---

## 🧠 Regra de Ouro

Quando a questão parecer confusa, faça três perguntas:

1. **É transacional ou analítico?**
2. **É relacional ou NoSQL?**
3. **O dado está no S3 ou precisa estar em um banco?**

Depois disso, os candidatos começam a desaparecer sozinhos.

**Transação → RDS / Aurora / DynamoDB**

**Analytics → Redshift**

**SQL no S3 → Athena**

**Cache → ElastiCache / DAX**

**Big Data distribuído → EMR**

Papo reto: na CLF-C02, você não precisa decorar cada detalhe de implementação.

Precisa reconhecer **qual problema cada serviço resolve**.

Se você dominar isso, metade dos distratores já morre na largada.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 5: Lab - Alta Disponibilidade com RDS Multi-AZ](10-lab-criando-banco-rds-multi-az.md)
* [➡️ Módulo 6: ](../06-redes-e-conectividade/00-vpc-rede-privada-virtual-isolada.md)

---
---