# RDS vs. DynamoDB: O Duelo de Titãs dos Bancos de Dados

No mundo do desenvolvimento, escolher o banco de dados errado é como tentar atravessar o oceano de canoa. Você até pode conseguir, mas o sofrimento vai ser grande.

Na AWS, uma das comparações mais importantes para a CLF-C02 é entre o **Amazon RDS** e o **Amazon DynamoDB**.

O RDS representa o mundo dos **bancos relacionais**. O DynamoDB representa o mundo **NoSQL**, baseado principalmente em modelos de chave-valor e documentos.

A ideia aqui não é descobrir qual é "melhor". É entender **qual banco combina com cada tipo de problema**.

---

## 1. Matriz Comparativa: Relational vs NoSQL

Aqui está a bússola para você não se perder nos requisitos técnicos:

| Pilar | Amazon RDS (Relacional) | Amazon DynamoDB (NoSQL) |
| :--- | :--- | :--- |
| **Modelo de Dados** | Tabelas com linhas e colunas, consultadas com SQL. | Modelo de **chave-valor** e **documentos**. |
| **Esquema** | Estruturado e definido previamente. | Flexível: os itens podem possuir atributos diferentes. |
| **Escalabilidade** | Pode escalar verticalmente e também utilizar estratégias de escala horizontal, dependendo do mecanismo e da arquitetura. | Escala horizontalmente por meio de partições e recursos gerenciados pela AWS. |
| **Relacionamentos** | Suporta **JOINs**, chaves estrangeiras e integridade referencial. | Não é projetado para JOINs; é otimizado para acessos baseados nas chaves e padrões de acesso definidos. |
| **Latência** | Depende da carga, consulta, mecanismo e configuração. | Projetado para oferecer latência de **milissegundos de um dígito** em grande escala. |
| **Operação** | Serviço gerenciado: a AWS administra a infraestrutura, mas você escolhe e configura a instância. | **Serverless**: não há servidores de banco para provisionar ou administrar. |

### A diferença de mentalidade

No RDS, normalmente você pensa primeiro:

> "Quais são minhas tabelas e como elas se relacionam?"

No DynamoDB, a pergunta muda:

> "Como minha aplicação vai consultar esses dados?"

Isso é importante porque o DynamoDB não foi projetado para você simplesmente pegar um modelo relacional e jogar dentro dele.

No DynamoDB, **os padrões de acesso da aplicação influenciam diretamente o desenho da tabela e das chaves**.

> **Pulo do gato:** não pense "RDS = pequeno" e "DynamoDB = grande". Os dois conseguem operar em grande escala. A diferença principal está no **modelo de dados e na forma como a aplicação acessa esses dados**.

---

## 2. Critérios de Decisão: Quando Escolher o quê?

Se você estiver na dúvida durante a prova, não tente decorar uma lista gigantesca.

Olhe para **como a aplicação precisa trabalhar com os dados**.

### Vá de Amazon RDS se:

- A aplicação precisa de **JOINs complexos** entre várias tabelas, como um ERP relacionando clientes, pedidos e produtos.
- Você precisa de um banco **relacional** com SQL e suporte a transações.
- O modelo de dados possui relacionamentos bem definidos e um esquema relativamente estável.
- A aplicação já utiliza **MySQL, PostgreSQL, MariaDB, Oracle ou SQL Server** e você quer migrá-la para a AWS com poucas alterações.
- O sistema depende de recursos típicos de bancos relacionais, como **integridade referencial** e consultas complexas.

### Vá de Amazon DynamoDB se:

- A aplicação precisa lidar com **grandes volumes de requisições** e escala horizontal.
- O padrão de acesso aos dados é conhecido e pode ser modelado em torno de **chaves**.
- Você precisa de latência de **milissegundos de um dígito** em grande escala.
- A carga pode variar bastante e você quer utilizar o modo **On-Demand**, pagando conforme o uso.
- A aplicação trabalha com casos como **IoT, aplicações mobile, carrinhos de compras, sessões e jogos**.

> **Atenção:** o esquema flexível do DynamoDB não significa "não preciso pensar no modelo de dados". É justamente o contrário. Definir corretamente as **chaves e os padrões de acesso** é fundamental para aproveitar o DynamoDB.

---

## 3. Cenários de "Gabarito" para a Prova

A banca pode não perguntar diretamente:

> "Qual banco é NoSQL?"

Ela pode contar uma história e esperar que você reconheça o cenário.

### Cenário A — Carrinho de compras com picos enormes

> "Uma empresa precisa de um banco de dados para um carrinho de compras que suporte picos de tráfego durante a Black Friday, com baixa latência e sem gerenciamento de servidores."

**Resposta:** **Amazon DynamoDB**

**Gatilhos:**

- Serverless.
- Escala horizontal.
- Baixa latência.
- Grande volume de requisições.
- Carga variável, que pode se beneficiar do modo **On-Demand**.

---

### Cenário B — ERP com relacionamentos complexos

> "Um sistema de ERP corporativo precisa executar consultas SQL e gerar relatórios cruzando dados de vendas, clientes e estoque."

**Resposta:** **Amazon RDS**

**Gatilhos:**

- SQL.
- Múltiplas tabelas.
- Relacionamentos.
- JOINs.
- Consultas complexas.

Aqui o DynamoDB estaria sendo usado como uma chave de fenda para apertar parafuso de estrela. Dá para tentar, mas... não. 😂

---

### Cenário C — Aplicação de jogos com baixa latência

> "Um aplicativo de jogos precisa armazenar perfis de jogadores e informações de partidas, suportando milhões de usuários com baixa latência."

**Resposta provável:** **Amazon DynamoDB**

**Gatilhos:**

- Grande escala.
- Muitas requisições.
- Baixa latência.
- Aplicação mobile.
- Modelo NoSQL.

Mas cuidado: **"jogo" sozinho não significa DynamoDB**.

Se o enunciado falar em relacionamentos complexos, JOINs ou consultas relacionais, o cenário pode apontar para um banco relacional.

---

## 4. RDS vs. DynamoDB em uma Frase

Se você precisar guardar uma única regra na cabeça para a prova, guarde esta:

> **RDS:** dados relacionais, SQL, JOINs e transações estruturadas.
>
> **DynamoDB:** alta escala, baixa latência, acesso orientado por chave e operação Serverless.

Essa distinção resolve uma boa parte das questões de comparação entre os dois serviços.

---

## 🎯 Gatilho de Exame

Foque nesses termos em inglês para eliminar as alternativas erradas:

- **Relational database:** Pense em **RDS**, tabelas, SQL e relacionamentos.
- **NoSQL database:** Pense em **DynamoDB**, chave-valor e documentos.
- **JOINs:** Forte indicação de banco relacional.
- **Schema flexibility:** O DynamoDB permite que diferentes itens possuam atributos diferentes.
- **Horizontal scaling:** DynamoDB distribui os dados e a carga entre partições.
- **Vertical scaling:** Em RDS, aumentar a capacidade da instância é uma estratégia comum de escala.
- **Serverless database:** Forte indicação de **DynamoDB** quando o cenário não exige um banco relacional.
- **On-Demand:** DynamoDB pode ajustar a capacidade de leitura e gravação conforme a demanda, sem necessidade de provisionar capacidade antecipadamente.
- **Single-digit millisecond latency:** Um dos principais gatilhos para DynamoDB.

> **Sinal de Alerta:** não marque DynamoDB simplesmente porque a questão fala em "grande escala". Primeiro procure o **modelo de dados e o padrão de acesso**.
>
> Se o enunciado falar em **JOINs complexos, múltiplas tabelas e relacionamentos**, pense em **RDS**.
>
> Se falar em **grande escala, baixa latência, chave-valor/documentos e acesso orientado por chave**, pense em **DynamoDB**.
>
> Essa é uma das comparações que mais vale a pena dominar para a CLF-C02.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 5: Amazon QuickSight - BI na Velocidade da Nuvem](07-visualizacao-de-dados-quicksight.md)
* [➡️ Módulo 5: Mnemônicos e Regras de Ouro - Bancos de Dados e Analytics](09-mnemonicos-bancos-de-dados.md)

---
---