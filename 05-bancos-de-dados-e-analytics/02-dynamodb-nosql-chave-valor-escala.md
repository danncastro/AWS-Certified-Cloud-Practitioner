# Amazon DynamoDB: NoSQL, Chave-Valor e Escala Monstruosa

Esqueça aquela imagem de um banco relacional gigantesco cheio de `JOIN`, tabelas relacionadas e servidores que você precisa ficar dimensionando.

O **Amazon DynamoDB** é o banco de dados **NoSQL totalmente gerenciado** da AWS, projetado para aplicações que precisam de **baixa latência, alta disponibilidade e escala horizontal**.

Você não gerencia servidor, sistema operacional ou infraestrutura de banco. Cria a tabela, define como os dados serão acessados e a AWS cuida da infraestrutura por baixo.

É o tipo de banco pensado para aplicações que podem sair de poucas requisições para milhões de operações sem você precisar ficar redimensionando servidor na mão.

> **Pense assim:** DynamoDB = **NoSQL + baixa latência + escala massiva + operação simplificada**.

---

## 1. O que torna o DynamoDB insano?

O DynamoDB não é simplesmente "um banco sem SQL".

A grande sacada é que ele foi construído para entregar **baixa latência e escala massiva**, sem você precisar administrar servidores de banco de dados.

### ⚡ Baixa latência

O DynamoDB foi projetado para oferecer **latência de milissegundos de um único dígito (single-digit milliseconds)** para operações típicas.

Isso o torna interessante para aplicações que precisam responder rapidamente, como:

- **Carrinho de compras:** consultar e atualizar itens rapidamente durante a navegação.
- **Jogos online:** armazenar estados e informações dos jogadores com baixa latência.
- **Aplicações web:** consultar dados frequentemente sem depender de um banco relacional tradicional.
- **Sistemas de alta escala:** processar grandes volumes de requisições sem precisar administrar servidores de banco.

> **Gatilho de prova:** apareceu **"single-digit millisecond latency"** junto com **NoSQL** e **alta escala**? DynamoDB deve acender a luzinha na cabeça.

### ☁️ Serverless por natureza

Você não precisa:

- criar EC2;
- instalar banco de dados;
- escolher CPU ou memória;
- aplicar patches no sistema operacional;
- configurar armazenamento de disco;
- administrar servidores de banco.

Você trabalha com o DynamoDB através da **API, SDK ou ferramentas da AWS**.

A infraestrutura necessária para executar o banco fica por conta da AWS.

> **Pegadinha:** "Serverless" não significa que **não existem servidores**. Significa que **você não precisa gerenciá-los**.

### 🛡️ Alta disponibilidade

O DynamoDB foi projetado para ser altamente disponível.

Os dados são armazenados de forma redundante dentro de uma **Região da AWS**, utilizando múltiplas **Availability Zones (AZs)**.

Isso significa que uma falha de uma AZ não exige que você faça um failover manual para continuar utilizando a tabela.

E aqui está uma distinção importante:

- **DynamoDB dentro de uma Região:** alta disponibilidade entre AZs.
- **DynamoDB Global Tables:** replicação entre **Regiões da AWS**.

Não misture os dois na prova.

### 📈 Escala horizontal

O DynamoDB foi projetado para escalar horizontalmente conforme a demanda.

Em vez de pensar:

> "Preciso de um servidor maior."

Pense:

> "Preciso que o serviço distribua a carga entre mais recursos."

É justamente essa arquitetura que permite ao DynamoDB atender workloads extremamente grandes.

---

## 2. Estrutura de Dados (Sem Mistério)

Aqui está uma das partes mais importantes para entender o DynamoDB.

Se você vem de SQL, pense na seguinte tradução:

| DynamoDB | Banco Relacional |
|---|---|
| **Table** | Tabela |
| **Item** | Linha/registro |
| **Attribute** | Coluna/campo |
| **Primary Key** | Chave primária |

Mas cuidado: **não tente transformar DynamoDB em um SQL sem JOIN**.

O modelo de dados é diferente.

### 📦 Tables

A **Table** é onde os dados são armazenados.

Por exemplo:

- `Users`
- `Orders`
- `Products`

Uma tabela pode armazenar milhões ou bilhões de itens sem que você precise criar manualmente dezenas de servidores.

### 📄 Items

Um **Item** representa um registro dentro da tabela.

No mundo SQL, você provavelmente chamaria isso de uma **linha**.

Exemplo:

~~~text
UserID = 123
Name   = Mano
Email  = mano@example.com
~~~

### 🏷️ Attributes

Os **Attributes** são os dados que pertencem ao item.

E aqui aparece uma diferença importante em relação ao SQL:

**DynamoDB possui um modelo de esquema flexível.**

Dois itens da mesma tabela podem possuir atributos diferentes.

Por exemplo:

~~~text
Item 1
UserID = 123
Name   = Mano
Email  = mano@example.com

Item 2
UserID = 456
Name   = João
Phone  = 11999999999
~~~

Isso não significa que você pode ignorar o desenho dos dados.

Muito pelo contrário.

No DynamoDB, você normalmente **projeta os dados pensando primeiro em como a aplicação fará as consultas**.

> Essa ideia é extremamente importante: **DynamoDB é orientado ao padrão de acesso**.

---

## 🔑 Chave Primária (Primary Key)

Todo item precisa ser identificável por uma **Primary Key**.

No DynamoDB, existem dois formatos principais.

### 1. Simple Primary Key

Possui apenas uma **Partition Key**.

Exemplo:

~~~mermaid
flowchart TD
    P["🔑 Partition Key"] --> U["👤 UserID"]
~~~

Se `UserID` for a Partition Key, cada item precisa possuir um valor diferente de `UserID`.

### 2. Composite Primary Key

Combina:

- **Partition Key**
- **Sort Key**

Exemplo:

~~~mermaid
flowchart TD

    P["🔑 Partition Key"] --> U["UserID"]
    S["🔑 Sort Key"] --> D["OrderDate"]

    U --> K["🗝️ Primary Key<br/>Composite Key"]
    D --> K
~~~

Isso permite armazenar vários itens com a mesma Partition Key, desde que a combinação entre Partition Key e Sort Key seja única.

Imagine:

~~~text
UserID = 123 | OrderDate = 2026-08-01
UserID = 123 | OrderDate = 2026-08-05
UserID = 123 | OrderDate = 2026-08-14
~~~

Todos pertencem ao mesmo usuário, mas possuem diferentes valores de Sort Key.

### 🧠 A analogia que ajuda

Pense em um armário:

~~~text
Partition Key = gaveta
Sort Key      = ordem dentro da gaveta
~~~

A **Partition Key** ajuda o DynamoDB a localizar e distribuir o conjunto de dados.

A **Sort Key** permite organizar e consultar os itens associados à mesma Partition Key.

### Partition Key

A **Partition Key** é utilizada pelo DynamoDB para distribuir os dados entre as partições.

Por isso, escolher uma boa chave é fundamental.

Uma chave com valores bem distribuídos ajuda a evitar que uma única partição receba carga excessiva.

> **Pegadinha:** não pense que Partition Key significa simplesmente "o lugar físico onde o dado fica". Ela participa do mecanismo que o DynamoDB utiliza para distribuir e localizar os dados.

### Sort Key

A **Sort Key** é opcional.

Quando utilizada, permite organizar e consultar itens que possuem a mesma Partition Key.

Um exemplo clássico:

~~~text
Partition Key = UserID
Sort Key      = OrderDate
~~~

Assim:

~~~text
UserID = 123
├── 2026-08-01
├── 2026-08-05
└── 2026-08-14
~~~

Esse padrão é muito útil quando existe uma relação natural entre uma entidade e vários registros associados.

---

## 🔎 Índices

O DynamoDB também possui índices para permitir consultas utilizando atributos que não fazem parte da chave primária original.

Os dois principais são:

| Índice | Característica |
|---|---|
| **GSI — Global Secondary Index** | Pode utilizar uma chave diferente da tabela e pode ser criado ou removido conforme necessário |
| **LSI — Local Secondary Index** | Utiliza a mesma Partition Key da tabela, mas permite uma Sort Key diferente |

Para a CLF-C02, o mais importante é reconhecer que **índices permitem consultar os dados por outras chaves além da Primary Key original**.

Não precisa transformar isso em uma tese de DynamoDB agora. 😅

---

## 3. Modos de Capacidade: Dinheiro vs. Performance

A banca adora cobrar como você paga pelo DynamoDB.

Existem dois modos principais:

### 💰 Provisioned Capacity

Você define a capacidade desejada de leitura e escrita utilizando:

- **RCUs — Read Capacity Units**
- **WCUs — Write Capacity Units**

É interessante quando você possui uma carga relativamente previsível e quer controlar a capacidade provisionada.

Você também pode utilizar **DynamoDB Auto Scaling** para ajustar automaticamente a capacidade provisionada conforme a utilização.

~~~mermaid
flowchart TD

    W["📊 Workload previsível"]
        --> P["⚙️ Provisioned Capacity"]

    P --> C["📦 Capacidade provisionada"]
    
    C --> R["📥 RCU<br/>Read Capacity Units"]
    C --> U["📤 WCU<br/>Write Capacity Units"]

    R --> A["📈 Auto Scaling<br/>(opcional)"]
    U --> A
~~~

**Exemplo:**

Uma aplicação corporativa recebe aproximadamente o mesmo volume de requisições durante o horário comercial.

Nesse cenário, Provisioned Capacity pode fazer sentido.

### ⚡ On-Demand Capacity

No modo **On-Demand**, você não precisa definir antecipadamente RCUs e WCUs.

O DynamoDB gerencia a capacidade para acompanhar a demanda, e você paga pelas operações realizadas.

É especialmente interessante para:

- **Workloads imprevisíveis:** você não sabe quando os picos vão acontecer.
- **Aplicações novas:** ainda não existem métricas suficientes para estimar a capacidade.
- **Tráfego variável:** a aplicação pode ficar praticamente parada e depois receber um pico enorme.

~~~mermaid
flowchart TD

    D["📈 Demanda imprevisível"]
        --> O["⚡ On-Demand"]

    O --> P["💰 Paga pelas requisições"]
~~~

> **Pegadinha de prova:**  
> **Provisioned** = você define capacidade.  
> **On-Demand** = você não precisa provisionar capacidade antecipadamente.

---

## 🆚 Provisioned vs. On-Demand

| Característica | Provisioned | On-Demand |
|---|---|---|
| Define capacidade antecipadamente | ✅ Sim | ❌ Não |
| RCUs/WCUs | ✅ Sim | Gerenciadas pelo serviço |
| Auto Scaling | ✅ Pode utilizar | Não é necessário |
| Carga previsível | 🟢 Excelente opção | 🟡 Pode ser usado |
| Carga imprevisível | 🟡 Pode exigir ajuste | 🟢 Excelente opção |
| Pagamento | Pela capacidade provisionada | Pelas requisições |

---

## 🌎 Global Tables

E se a aplicação precisar operar em **múltiplas Regiões da AWS**?

Aí entra o **DynamoDB Global Tables**.

Ele permite replicar os dados entre Regiões, possibilitando arquiteturas **multi-Region** com leitura e escrita nas diferentes Regiões.

Um cenário clássico seria:

~~~mermaid
flowchart TD

    G["🌎 DynamoDB Global Tables"]

    G --> USE["🇺🇸 us-east-1"]
    G --> BR["🇧🇷 sa-east-1"]

    USE --> APP1["🖥️ Aplicação"]
    BR --> APP2["🖥️ Aplicação"]

    classDef global fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef region fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef app fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;

    class G global;
    class USE,BR region;
    class APP1,APP2 app;
~~~

**Gatilho de exame:**

> "Banco NoSQL global, replicação automática entre Regiões e aplicações realizando leitura e escrita localmente."

👉 **DynamoDB Global Tables**

---

## 🚀 DAX — DynamoDB Accelerator

O **DAX (DynamoDB Accelerator)** é um cache totalmente gerenciado criado especificamente para o DynamoDB.

Ele fica na frente da tabela e pode acelerar workloads de leitura intensiva.

A ideia é simples:

~~~mermaid
flowchart TD

    APP["🖥️ Aplicação"]
        --> DAX["⚡ DynamoDB Accelerator (DAX)"]

    DAX -->|Cache Hit| HIT["🚀 Resposta rápida"]

    DAX -->|Cache Miss| DB["🗄️ Amazon DynamoDB"]

    classDef app fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef dax fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef hit fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;
    classDef db fill:#F3E5F5,stroke:#8E24AA,stroke-width:2px;

    class APP app;
    class DAX dax;
    class HIT hit;
    class DB db;
~~~ 

É especialmente útil quando a aplicação consulta repetidamente os mesmos dados.

> **Gatilho de exame:** se a questão falar em **cache para DynamoDB**, **microssegundos** e aplicação com muitas leituras repetidas, pense em **DAX**.

---

## 🎯 Gatilho de Exame

Identifique o DynamoDB na prova por estes termos:

- **Amazon DynamoDB:** banco de dados NoSQL totalmente gerenciado e serverless.
- **NoSQL key-value / document database:** modelo de dados baseado em chave-valor e documentos.
- **Single-digit millisecond latency:** baixa latência para operações típicas.
- **Serverless database:** você não gerencia servidores ou infraestrutura de banco.
- **Partition Key:** utilizada para identificar e distribuir os dados.
- **Sort Key:** organiza e permite consultar itens associados à mesma Partition Key.
- **Provisioned Capacity:** capacidade definida por RCUs/WCUs.
- **On-Demand Capacity:** pagamento baseado nas operações realizadas, sem necessidade de provisionar capacidade antecipadamente.
- **Global Tables:** replicação entre Regiões para arquiteturas multi-Region.
- **DAX:** cache especializado para DynamoDB, indicado para workloads de leitura intensiva e baixa latência.

---

## 🚨 Sinal de Alerta

DynamoDB **NÃO é um banco relacional**.

Se a questão falar em:

- **SQL tradicional**
- **JOINs complexos**
- **relacionamentos relacionais**
- **integridade referencial**
- **modelo relacional**

comece a pensar em **Amazon RDS** ou **Amazon Aurora**, dependendo do cenário.

Já se aparecer:

- **NoSQL**
- **chave-valor**
- **documentos**
- **escala massiva**
- **baixa latência**
- **serverless**
- **Partition Key / Sort Key**

👉 **DynamoDB.**

> **Mantra para a prova:**  
> **RDS/Aurora → relacional.**  
> **DynamoDB → NoSQL + escala + baixa latência.**

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 5: Amazon Aurora - Performance e Resiliência Nativa](01-aurora-performance-e-resiliencia-nativa.md)
* [➡️ Módulo 5: Amazon Redshift - Data Warehousing e Analytics em Larga Escala](03-redshift-data-warehousing-analytics.md)

---
---