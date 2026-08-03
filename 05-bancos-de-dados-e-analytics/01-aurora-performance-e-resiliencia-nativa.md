# Amazon Aurora: Performance e Resiliência Nativa

Se o **Amazon RDS** já elimina boa parte da dor de cabeça de administrar um banco de dados, o **Amazon Aurora** leva isso para outro nível. Pense assim: se o RDS tradicional é um carro esportivo, o Aurora é um Fórmula 1 construído especialmente para correr na infraestrutura da AWS.

Ele não é apenas o MySQL ou o PostgreSQL rodando em uma instância EC2. O Aurora é um banco de dados relacional **Cloud-native**, desenvolvido pela própria AWS para entregar mais desempenho, maior disponibilidade e alta resiliência, mantendo compatibilidade com aplicações que utilizam **MySQL** ou **PostgreSQL**.

Na prática, a proposta é simples: oferecer a performance e a confiabilidade de bancos comerciais de alto nível, como Oracle Enterprise, mas preservando a simplicidade dos bancos de código aberto.

---

## 1. O que faz o Aurora ser diferente?

O Aurora foi projetado para resolver limitações comuns dos bancos relacionais tradicionais. Estes são os diferenciais que mais aparecem na CLF-C02.

### 🚀 Performance Superior

O Aurora entrega:

- Até **5 vezes mais desempenho** que o MySQL padrão.
- Até **3 vezes mais desempenho** que o PostgreSQL padrão, utilizando hardware equivalente.

Isso é possível porque sua arquitetura de armazenamento foi desenvolvida especificamente para a infraestrutura da AWS, reduzindo gargalos comuns dos bancos tradicionais.

---

### 📈 Armazenamento com Escalabilidade Automática

No Aurora, você normalmente não precisa se preocupar em aumentar o tamanho do disco manualmente.

O armazenamento cresce automaticamente conforme os dados aumentam, começando em **10 GB** e chegando até **128 TB**, sem necessidade de interrupção da aplicação.

> Essa é uma diferença importante em relação ao Amazon RDS tradicional, onde normalmente existe maior preocupação com o provisionamento do armazenamento.

---

### 🛡️ Resiliência Nativa

Este é, provavelmente, o principal diferencial cobrado na prova.

Cada gravação realizada no banco é distribuída automaticamente para **6 cópias dos dados**, espalhadas entre **3 Availability Zones (AZs)**.

Essa arquitetura permite que o Aurora continue funcionando mesmo diante de falhas de:

- discos;
- servidores;
- uma Availability Zone inteira.

É justamente essa distribuição automática que torna o Aurora extremamente resiliente.

---

### 🔧 Auto-Cura (Self-Healing)

O Aurora monitora continuamente seu armazenamento.

Caso identifique algum bloco de dados corrompido, ele recupera automaticamente esse bloco utilizando uma das demais cópias saudáveis, sem necessidade de intervenção manual e, na maioria dos casos, sem impacto perceptível para a aplicação.

---

## 2. Escalabilidade de Leitura e Failover

Agora imagine outro cenário.

Sua aplicação cresceu e milhares de usuários estão acessando o banco ao mesmo tempo. O problema não são as gravações, mas sim a quantidade enorme de consultas (**SELECTs**).

É exatamente aí que entram as **Aurora Replicas**.

### Aurora Replicas (Foco: Escalabilidade de Leitura)

O Aurora suporta até **15 réplicas de leitura**, permitindo distribuir consultas entre várias instâncias.

Esse modelo é ideal para aplicações que possuem:

- muitos usuários consultando informações;
- poucas gravações;
- necessidade de aumentar a capacidade de leitura sem alterar a aplicação.

---

### Failover Automático

Se a instância principal apresentar falha, o Aurora promove automaticamente uma das réplicas para instância principal.

Como todas compartilham o mesmo armazenamento distribuído, essa troca acontece rapidamente, reduzindo significativamente o tempo de indisponibilidade da aplicação.

> **Pegadinha de prova:** Não confunda **Read Replica** com **Backup**. As réplicas existem para aumentar a capacidade de leitura e também podem participar do failover automático.

---

## 3. Aurora Serverless: Economia para Cargas Variáveis

Nem toda aplicação possui um volume constante de acessos.

Algumas ficam praticamente o dia inteiro sem uso e, em determinados horários, recebem milhares de requisições.

Nesses casos, o **Aurora Serverless** pode ser uma excelente escolha.

Ao invés de definir previamente o tamanho da instância, você informa apenas a faixa de capacidade desejada.

A AWS faz todo o restante automaticamente.

Entre as principais vantagens estão:

- aumento automático da capacidade quando a demanda cresce;
- redução automática quando o tráfego diminui;
- cobrança proporcional ao uso da capacidade computacional.

Esse modelo é especialmente interessante para:

- aplicações com uso imprevisível;
- ambientes de desenvolvimento;
- aplicações utilizadas apenas em determinados horários.

---

## 🎯 Gatilho de Exame

Associe rapidamente estes conceitos:

- **Amazon Aurora:** Banco de dados relacional Cloud-native compatível com MySQL e PostgreSQL.
- **High Performance Database:** Até **5x** mais rápido que MySQL e até **3x** mais rápido que PostgreSQL.
- **Six copies across three AZs:** Replicação automática dos dados em **6 cópias distribuídas por 3 Availability Zones**.
- **Automatic Scaling Storage:** Armazenamento cresce automaticamente até **128 TB**.
- **Aurora Replicas:** Até **15 réplicas** para escalar consultas de leitura.
- **Automatic Failover:** Promoção automática de uma réplica caso a instância principal falhe.
- **Aurora Serverless:** Capacidade computacional ajustada automaticamente conforme a demanda.
- **MySQL/PostgreSQL Compatible:** Aplicações compatíveis normalmente exigem poucas alterações para migrar para o Aurora.

> **Sinal de Alerta:** A banca gosta de colocar **Amazon RDS**, **Amazon Aurora** e **Amazon DynamoDB** na mesma questão.
>
> - Precisa de um banco **Relacional (SQL)** → **Amazon RDS** ou **Amazon Aurora**.
> - Precisa de **máxima performance, alta disponibilidade nativa e arquitetura otimizada para AWS** → **Amazon Aurora**.
> - Precisa de um banco **NoSQL** → **Amazon DynamoDB**.
>
> Outra pegadinha comum é afirmar que o Aurora é um banco NoSQL. **Isso é falso.** O Aurora continua sendo um banco **relacional (SQL)**.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 5: Amazon RDS: Banco Relacional Gerenciado (SQL)](00-rds-banco-relacional-gerenciado-sql.md)
* [➡️ Módulo 5: ](02-dynamodb-nosql-chave-valor-escala.md)

---
---