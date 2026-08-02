# Opções de Compra EC2 e a Regra de Ouro Spot

Escolher a opção de compra correta para uma instância EC2 é tão importante quanto escolher o tipo da instância. A decisão impacta diretamente o custo, a disponibilidade e até mesmo a continuidade da aplicação.

A AWS oferece diferentes modelos de cobrança para atender desde ambientes de desenvolvimento até aplicações críticas de produção. Saber identificar qual modalidade usar em cada cenário é uma das habilidades mais cobradas na CLF-C02.

---

## 1. As 4 Opções de Compra do EC2

Cada modalidade foi criada para um tipo específico de necessidade. Entender quando utilizar cada uma é muito mais importante do que decorar percentuais de desconto.

### On-Demand Instances

As **On-Demand Instances** funcionam no modelo "pagou, usou".

Você paga apenas pelo tempo em que a instância permanece ligada, sem contratos ou compromissos de longo prazo.

É a opção ideal para:

- Ambientes de desenvolvimento;
- Testes e laboratórios;
- Aplicações com carga imprevisível;
- Projetos novos cujo consumo ainda é desconhecido.

Apesar de oferecer máxima flexibilidade, normalmente é a opção com o maior custo por hora.

---

### Reserved Instances (RIs) e Savings Plans

Se a aplicação ficará ligada continuamente durante meses ou anos, faz sentido assumir um compromisso de uso.

Nesse cenário entram as **Reserved Instances (RIs)** e os **Savings Plans**, que oferecem descontos significativos em troca de um compromisso de **1 ou 3 anos**, podendo chegar a aproximadamente **72%**.

São ideais para:

- Bancos de dados;
- Aplicações corporativas;
- Servidores de produção;
- Workloads previsíveis.

#### Savings Plans

Os **Savings Plans** são considerados a evolução das Reserved Instances.

Em vez de reservar uma instância específica, você assume um compromisso de consumo por hora (USD/hora), permitindo que o desconto seja aplicado em diferentes serviços de computação, como:

- Amazon EC2;
- AWS Fargate;
- AWS Lambda.

Essa flexibilidade faz com que, na prática, muitas empresas prefiram Savings Plans às Reserved Instances tradicionais.

---

### Spot Instances

As **Spot Instances** utilizam capacidade ociosa dos datacenters da AWS.

Como essa capacidade pode ser retomada pela AWS a qualquer momento, o desconto pode chegar a **90%**.

O ponto mais importante é que a AWS pode interromper a instância sempre que precisar daquela capacidade.

Antes disso, ela envia um aviso com aproximadamente **2 minutos de antecedência**, permitindo que a aplicação realize um desligamento controlado.

É justamente essa característica que torna as Spot extremamente econômicas, mas inadequadas para aplicações críticas.

---

### Dedicated Hosts / Dedicated Instances

As **Dedicated Hosts** e **Dedicated Instances** utilizam hardware físico dedicado exclusivamente à sua conta AWS.

Nenhum outro cliente compartilha aquele servidor físico.

Esse modelo normalmente é utilizado quando existem requisitos de:

- Compliance;
- Regulamentações específicas;
- Licenciamento de software (**BYOL - Bring Your Own License**);
- Isolamento físico da infraestrutura.

É também a opção com maior custo entre todas as modalidades de compra.

---

## 2. A Regra de Ouro das Spot Instances

Muitos candidatos erram questões da prova porque associam automaticamente "menor preço" com "melhor escolha".

Com Spot isso não funciona.

A regra é simples:

> **Spot só deve ser utilizada em cargas de trabalho tolerantes à interrupção (Fault-Tolerant Workloads).**

Isso significa que a aplicação precisa conseguir continuar funcionando mesmo que uma instância seja encerrada inesperadamente.

### Onde usar Spot

As Spot Instances são excelentes para:

- Processamento em lote (Batch Jobs);
- Renderização de vídeos ou imagens;
- Computação científica;
- Big Data;
- Machine Learning;
- Ambientes de desenvolvimento;
- Pipelines de CI/CD;
- Testes automatizados.

Caso uma instância seja interrompida, outra pode assumir o processamento ou o trabalho pode ser reiniciado sem grandes impactos.

### Onde NÃO usar Spot

Evite utilizar Spot para aplicações que precisam permanecer disponíveis continuamente, como:

- Bancos de dados relacionais;
- Aplicações críticas de produção;
- Sistemas monolíticos com inicialização demorada;
- Serviços que não toleram interrupções.

Nestes casos, o desconto não compensa o risco de indisponibilidade.

---

## 3. Comparativo das Opções de Compra

| Opção | Melhor cenário |
|--------|----------------|
| **On-Demand** | Desenvolvimento, testes e cargas imprevisíveis |
| **Reserved Instances** | Workloads estáveis e previsíveis |
| **Savings Plans** | Economia com maior flexibilidade entre serviços |
| **Spot Instances** | Workloads tolerantes à interrupção |
| **Dedicated Hosts** | Compliance e licenciamento BYOL |

---

## 4. Casos Clássicos de Prova

### Cenário 1

> Preciso do menor custo possível e minha aplicação pode ser interrompida.

Resposta: **Spot Instances**

---

### Cenário 2

> Meu banco de dados ficará ligado durante anos.

Resposta: **Reserved Instances** ou **Savings Plans**

---

### Cenário 3

> Ainda não conheço o consumo da aplicação.

Resposta: **On-Demand Instances**

---

### Cenário 4

> Preciso utilizar licenças próprias (BYOL) e cumprir requisitos rígidos de compliance.

Resposta: **Dedicated Hosts**

---

### Cenário 5

> Quero economizar, mas também preciso de flexibilidade entre EC2, Lambda e Fargate.

Resposta: **Savings Plans**

---

## Resumo Rápido

| Opção | Compromisso | Economia | Interrupção |
|--------|-------------|-----------|-------------|
| On-Demand | ❌ | Baixa | Nunca pela modalidade |
| Reserved Instances | 1 ou 3 anos | Até 72% | Não |
| Savings Plans | 1 ou 3 anos | Até 72% | Não |
| Spot | Nenhum | Até 90% | Sim |
| Dedicated Hosts | Conforme contrato | Baixa | Não |

---

## O que costuma cair na prova?

A CLF-C02 normalmente cobra:

- diferença entre Spot e Reserved Instances;
- quando utilizar Savings Plans;
- cargas de trabalho ideais para Spot;
- Dedicated Hosts para compliance e BYOL;
- On-Demand para cargas imprevisíveis.

---

## 🎯 Gatilho de Exame

Se aparecer...

| Enunciado | Resposta |
|------------|----------|
| Unpredictable Workloads | On-Demand |
| No Long-Term Commitment | On-Demand |
| Predictable Usage | Reserved Instances |
| Steady-State Workload | Reserved Instances |
| Commitment (USD/hour) | Savings Plans |
| Flexible Across Compute Services | Savings Plans |
| Unused Compute Capacity | Spot Instances |
| Up to 90% Discount | Spot Instances |
| Fault-Tolerant Workloads | Spot Instances |
| Two-Minute Interruption Warning | Spot Instances |
| Physical Server | Dedicated Hosts |
| Bring Your Own License (BYOL) | Dedicated Hosts |

---

## Pegadinhas da Prova

| Se a questão perguntar... | Resposta |
|---------------------------|----------|
| Menor custo possível | Spot (desde que tolere interrupção) |
| Banco de dados em produção | Reserved Instances ou Savings Plans |
| Ambiente de testes | On-Demand ou Spot |
| Compromisso de 1 ou 3 anos | Reserved / Savings Plans |
| Licenciamento próprio (BYOL) | Dedicated Hosts |

---

> **💡 Dica de Ouro:** Antes de pensar no desconto, pergunte: **"Essa aplicação pode parar?"** Se a resposta for **sim**, considere **Spot Instances**. Se a resposta for **não**, pense em **Reserved Instances** ou **Savings Plans** para economizar sem abrir mão da disponibilidade.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 3: Amazon EC2 - Instâncias Virtuais na Prática](00-ec2-instancias-virtuais.md)
* [➡️ Módulo 3: ELB e Auto Scaling - O Combo da Alta Disponibilidade](02-auto-scaling-e-elastic-load-balancing.md)

---
---