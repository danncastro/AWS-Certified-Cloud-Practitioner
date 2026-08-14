# Amazon ElastiCache: Cache em Memória e Redis

Por mais tunado que esteja o seu banco de dados, **memória RAM é muito mais rápida do que armazenamento em disco**.

Agora imagine uma aplicação consultando "produtos mais vendidos" milhares de vezes por segundo.

Faz sentido mandar todas essas consultas para o banco principal?

**Não.**

É exatamente aí que entra o **Amazon ElastiCache**.

Ele fornece uma camada de **cache em memória** para armazenar temporariamente dados acessados com frequência, reduzindo a quantidade de consultas que chegam ao banco principal e diminuindo bastante a latência.

A ideia é simples:

~~~mermaid
flowchart LR

    APP["🖥️ Aplicação"]
        --> CACHE{"Existe no cache?"}

    CACHE -->|SIM| EC["⚡ Amazon ElastiCache"]
    CACHE -->|NÃO| DB["🗄️ Banco de Dados"]

    DB --> GET["🔎 Busca os dados"]
    GET --> UPDATE["🔄 Atualiza o cache"]

    EC --> RESULT["📦 Retorna dados"]
    UPDATE --> RESULT

    classDef app fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef decision fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef cache fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;
    classDef db fill:#F3E5F5,stroke:#8E24AA,stroke-width:2px;
    classDef process fill:#FCE4EC,stroke:#C2185B,stroke-width:2px;
    classDef result fill:#E0F2F1,stroke:#00796B,stroke-width:2px;

    class APP app;
    class CACHE decision;
    class EC cache;
    class DB db;
    class GET,UPDATE process;
    class RESULT result;
~~~

Se o dado já estiver no cache, a aplicação evita consultar o banco.

Resultado:

- **Menos carga no banco**
- **Menor latência**
- **Maior capacidade de atender requisições**
- **Melhor experiência para o usuário**

---

## 1. O que é o Amazon ElastiCache?

O **Amazon ElastiCache** é um serviço gerenciado de **cache em memória**.

Ele permite utilizar mecanismos de cache populares sem precisar administrar toda a infraestrutura por conta própria.

A AWS cuida de tarefas operacionais como:

- provisionamento da infraestrutura;
- manutenção;
- aplicação de patches;
- configuração do ambiente;
- monitoramento e operação do serviço.

O objetivo principal é simples:

> **Colocar dados frequentemente acessados na memória para que a aplicação consiga recuperá-los muito mais rapidamente.**

### ⚡ Por que memória?

Porque acessar dados que estão na RAM é muito mais rápido do que consultar repetidamente um banco armazenado em disco.

Imagine:

~~~mermaid
flowchart LR

    subgraph DB["🗄️ Acesso direto ao Banco"]
        D1["Banco de Dados"]
        D2["💾 Disco / DB"]
        D3["📊 Resultado"]

        D1 -->|"Consulta repetida"| D2
        D2 --> D3
    end

    subgraph CACHE["⚡ Acesso via Cache"]
        A1["🖥️ Aplicação"]
        A2["⚡ Cache"]
        A3["🧠 RAM"]
        A4["📊 Resultado"]

        A1 --> A2
        A2 --> A3
        A3 --> A4
    end

    classDef database fill:#F3E5F5,stroke:#8E24AA,stroke-width:2px;
    classDef storage fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef cache fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;
    classDef app fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef result fill:#E0F2F1,stroke:#00796B,stroke-width:2px;

    class D1 database;
    class D2 storage;
    class A1 app;
    class A2,A3 cache;
    class D3,A4 result;
~~~

O cache funciona como uma espécie de **atalho**.

Em vez de perguntar a mesma coisa ao banco milhares de vezes, a aplicação guarda temporariamente o resultado em memória.

---

## 2. Redis e Memcached

Aqui existe uma pegadinha importante para a CLF-C02.

O ElastiCache oferece mecanismos de cache baseados em **Redis** e **Memcached**.

Os dois trabalham em memória, mas possuem características diferentes.

| Característica | Redis | Memcached |
|---|---|---|
| Armazenamento em memória | ✅ | ✅ |
| Estruturas de dados avançadas | ✅ | Mais simples |
| Persistência | ✅ | ❌ |
| Replicação | ✅ | ❌ |
| Alta disponibilidade / failover | ✅ | ❌ |
| Pub/Sub | ✅ | ❌ |
| Sorted Sets | ✅ | ❌ |
| Uso como cache simples | ✅ | ✅ |

### 🟥 Redis

O **Redis** vai muito além de um cache simples.

Ele oferece estruturas de dados como:

- **Strings:** armazenamento simples de valores.
- **Lists:** listas ordenadas de elementos.
- **Sets:** conjuntos de valores únicos.
- **Hashes:** estruturas de chave e valor dentro de uma chave principal.
- **Sorted Sets:** conjuntos ordenados por pontuação, excelentes para rankings.

Além disso, o Redis suporta recursos como **persistência**, **replicação** e **Pub/Sub**.

Por isso, ele pode ser utilizado em cenários que exigem mais do que simplesmente guardar uma cópia temporária de um dado.

> **Gatilho mental:**  
> Redis = **estruturas de dados + persistência + replicação + recursos avançados**.

---

### 🟦 Memcached

O **Memcached** é mais simples.

Ele é focado em:

> **Cache rápido e simples em memória.**

Não possui os mesmos recursos avançados do Redis.

Se a aplicação só precisa armazenar valores temporários e simples para reduzir consultas ao banco, o Memcached pode ser suficiente.

> **Gatilho mental:**  
> Memcached = **cache simples e distribuído em memória**.

---

## 3. Cache Hit vs. Cache Miss

Esse conceito é fundamental para entender como o ElastiCache funciona.

### 🟢 Cache Hit

A aplicação procura um dado no cache e **encontra**.

~~~mermaid
flowchart LR

    APP["🖥️ Aplicação"]
        --> CACHE["⚡ Amazon ElastiCache"]

    CACHE -->|"Encontrou! ✅"| RESULT["📦 Retorna dado"]

    classDef app fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef cache fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;
    classDef result fill:#E0F2F1,stroke:#00796B,stroke-width:2px;

    class APP app;
    class CACHE cache;
    class RESULT result;
~~~

O banco principal nem precisa ser consultado.

---

### 🔴 Cache Miss

A aplicação procura um dado no cache, mas **não encontra**.

~~~mermaid
flowchart LR

    APP["🖥️ Aplicação"]
        --> CACHE["⚡ Amazon ElastiCache"]

    CACHE -->|"Não encontrou ❌"| DB["🗄️ Banco de Dados"]

    DB --> RESULT["📦 Retorna dado"]

    RESULT --> UPDATE["🔄 Atualiza o Cache"]

    classDef app fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef cache fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef db fill:#F3E5F5,stroke:#8E24AA,stroke-width:2px;
    classDef result fill:#E0F2F1,stroke:#00796B,stroke-width:2px;
    classDef update fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;

    class APP app;
    class CACHE cache;
    class DB db;
    class RESULT result;
    class UPDATE update;
~~~

A aplicação consulta o banco e, normalmente, coloca o resultado no cache para que a próxima solicitação possa ser atendida diretamente pela memória.

> **Cache Hit = encontrou no cache.**
>
> **Cache Miss = não encontrou e precisa buscar na origem.**

Essa diferença aparece bastante em questões que descrevem o comportamento de uma aplicação usando cache.

---

## 4. Casos de Uso

Agora vem a parte que realmente interessa para a prova:

**quando você usaria o ElastiCache?**

---

### A. 🚀 Aceleração de aplicações e redução da carga do banco

Esse é o cenário clássico.

Imagine uma aplicação que consulta constantemente:

> "Quais são os produtos mais vendidos?"

Se essa informação muda poucas vezes por minuto, não faz muito sentido consultar o banco milhares de vezes por segundo.

A aplicação pode:

1. verificar o ElastiCache;
2. retornar o resultado se houver um **Cache Hit**;
3. consultar o banco apenas quando houver um **Cache Miss**;
4. armazenar o novo resultado no cache.

Isso reduz a quantidade de consultas que chegam ao **RDS** ou **Aurora**.

~~~mermaid
flowchart LR

    APP["🖥️ Aplicação"]
        --> CACHE{"⚡ ElastiCache<br/>Cache Hit?"}

    CACHE -->|SIM ✅| HIT["📦 Retorna dados"]

    CACHE -->|NÃO ❌| DB["🗄️ Amazon RDS / Aurora"]

    DB --> UPDATE["🔄 Atualiza Cache"]

    UPDATE --> RESULT["📦 Retorna dados"]

    classDef app fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef cache fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef hit fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;
    classDef db fill:#F3E5F5,stroke:#8E24AA,stroke-width:2px;
    classDef update fill:#E0F2F1,stroke:#00796B,stroke-width:2px;

    class APP app;
    class CACHE cache;
    class HIT hit;
    class DB db;
    class UPDATE,RESULT update;
~~~

> **Objetivo principal:** tirar trabalho repetitivo do banco e entregar respostas mais rapidamente.

---

### B. 🔐 Armazenamento de sessões

Imagine uma aplicação rodando em várias instâncias:

~~~mermaid
flowchart LR

    LB["⚖️ Load Balancer"]

    LB --> EC1["🖥️ EC2-1"]
    LB --> EC2["🖥️ EC2-2"]
    LB --> EC3["🖥️ EC2-3"]

    classDef lb fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef ec2 fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;

    class LB lb;
    class EC1,EC2,EC3 ec2;
~~~

Se a sessão do usuário ficar armazenada localmente em apenas uma instância, surge um problema.

O usuário pode fazer uma nova requisição e cair em outro servidor.

Onde está a sessão?

Uma solução é utilizar o ElastiCache como um **armazenamento centralizado de sessões**.

Assim, qualquer instância da aplicação consegue acessar os dados da sessão.

~~~mermaid
flowchart LR

    EC1["🖥️ EC2-1"] --> CACHE["⚡ ElastiCache"]
    EC2["🖥️ EC2-2"] --> CACHE
    EC3["🖥️ EC2-3"] --> CACHE

    classDef ec2 fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef cache fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;

    class EC1,EC2,EC3 ec2;
    class CACHE cache;
~~~

Isso é especialmente útil em aplicações distribuídas e arquiteturas com múltiplas instâncias.

---

### C. 🏆 Leaderboards em tempo real

Imagine um jogo com milhares de jogadores.

Você precisa manter algo como:

~~~text
1º  João      9850 pontos
2º  Maria     9720 pontos
3º  Pedro     9510 pontos
4º  Lucas     9320 pontos
~~~

O Redis possui **Sorted Sets**, que são muito adequados para esse tipo de ranking.

A aplicação consegue atualizar as pontuações e consultar rapidamente a posição dos jogadores.

Por isso, **real-time leaderboards** é um ótimo cenário para lembrar de Redis.

---

### D. 📊 Dados frequentemente acessados

Outro cenário comum é quando determinados dados são consultados constantemente, mas sofrem poucas alterações.

Exemplos:

- catálogo de produtos;
- configurações de aplicação;
- informações de perfil;
- resultados de consultas caras;
- dados de referência utilizados repetidamente.

Em vez de consultar o banco toda vez, a aplicação pode manter esses dados temporariamente no cache.

> Quanto mais **frequente a leitura** e menor a frequência de alteração, maior tende a ser o benefício do cache.

---

## 5. Arquitetura Completa

Juntando tudo:

~~~mermaid
flowchart LR

    USER["👤 Usuário"]
        --> APP["🖥️ Web App"]

    APP -->|"1. Consulta"| CACHE["⚡ ElastiCache"]

    CACHE -->|"2. Cache Hit ✅"| APP

    CACHE -->|"3. Cache Miss ❌"| DB["🗄️ Amazon RDS / Aurora"]

    DB -->|"4. Retorna dados"| APP

    APP -->|"5. Armazena no Cache"| CACHE

    classDef user fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef app fill:#F3E5F5,stroke:#8E24AA,stroke-width:2px;
    classDef cache fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;
    classDef db fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;

    class USER user;
    class APP app;
    class CACHE cache;
    class DB db;
~~~

O fluxo é:

1. Usuário faz uma requisição.
2. Aplicação consulta o ElastiCache.
3. Se houver **Cache Hit**, retorna o dado rapidamente.
4. Se houver **Cache Miss**, consulta o banco.
5. A aplicação pode armazenar o resultado no cache.
6. Próximas requisições podem ser atendidas diretamente pela memória.

Essa arquitetura reduz a pressão sobre o banco principal.

---

## 🎯 Gatilho de Exame

Identifique o **Amazon ElastiCache** pelas seguintes pistas:

- **Amazon ElastiCache:** serviço gerenciado de cache em memória.
- **In-memory caching:** dados armazenados em memória para acesso rápido.
- **Reduce database load:** reduzir consultas repetitivas no RDS ou Aurora.
- **Low latency:** respostas muito rápidas para dados frequentemente acessados.
- **Cache Hit:** o dado foi encontrado no cache.
- **Cache Miss:** o dado não foi encontrado e precisa ser recuperado da origem.
- **Session store:** armazenamento centralizado de sessões para aplicações distribuídas.
- **Real-time leaderboards:** cenário clássico para Redis e Sorted Sets.
- **Redis:** estruturas de dados avançadas, persistência, replicação e recursos adicionais.
- **Memcached:** cache simples e distribuído em memória.

---

## 🆚 ElastiCache vs. DAX

Essa comparação merece atenção porque os dois aparecem em cenários de cache.

| Cenário | Serviço |
|---|---|
| Cache para aplicações em geral | **ElastiCache** |
| Cache na frente de RDS/Aurora | **ElastiCache** |
| Session store | **ElastiCache** |
| Leaderboards com Redis | **ElastiCache** |
| Cache especificamente para DynamoDB | **DAX** |
| Acelerar leituras do DynamoDB | **DAX** |

A regra mental é simples:

> **DynamoDB + cache dedicado → DAX**
>
> **Aplicação / RDS / Aurora + cache → ElastiCache**

---

## 🚨 Sinal de Alerta

Se a questão disser:

> "A aplicação realiza milhares de consultas repetidas ao RDS e precisa reduzir a carga do banco utilizando armazenamento em memória."

👉 **Amazon ElastiCache**

Se disser:

> "A aplicação precisa armazenar sessões compartilhadas entre várias instâncias."

👉 **Amazon ElastiCache**

Se disser:

> "O sistema precisa criar um ranking em tempo real utilizando estruturas de dados ordenadas."

👉 **ElastiCache com Redis**

Se disser:

> "Uma aplicação baseada em DynamoDB precisa de um cache dedicado para acelerar leituras."

👉 **DAX**

### 🧠 Mantra para a prova

**Cache em memória + aplicação → ElastiCache**

**Redis + estruturas de dados avançadas → ElastiCache**

**DynamoDB + cache dedicado → DAX**

**Cache Hit → encontrou**

**Cache Miss → não encontrou**

E lembre:

> **ElastiCache não substitui automaticamente seu banco de dados. Ele funciona como uma camada de aceleração na frente dele.**

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 5: Amazon Athena - Consultas SQL no S3 sem Servidores](04-athena-consultas-sql-no-s3-serverless.md)
* [➡️ Módulo 5: Amazon EMR - Processamento de Big Data com Hadoop e Spark](06-processamento-big-data-emr-hadoop.md)

---
---