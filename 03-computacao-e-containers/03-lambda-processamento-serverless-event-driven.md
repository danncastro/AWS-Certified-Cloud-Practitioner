# AWS Lambda: Processamento Serverless e Event-Driven

O **AWS Lambda** foi um divisor de águas na computação em nuvem. Ele popularizou o conceito de **"codar e esquecer a infraestrutura"**. Imagine que você tenha uma função que só precisa rodar quando alguém sobe uma foto no seu aplicativo. No modelo tradicional, seria necessário manter um servidor EC2 ligado 24 horas por dia esperando esse evento acontecer, pagando por ele mesmo quando ninguém estivesse usando. Com o Lambda, esse servidor simplesmente deixa de ser uma preocupação. O código executa, faz o trabalho necessário e encerra imediatamente. Você paga apenas pelo tempo de execução, alcançando o máximo de eficiência em custo e operação.

---

## 📑 Navegação

- [1. O que é o AWS Lambda?](#1-o-que-é-o-aws-lambda)
- [2. Os Pilares do Modelo Serverless e do Lambda](#2-os-pilares-do-modelo-serverless-e-do-lambda)
- [3. Limitações Críticas e Dimensionamento](#3-limitações-críticas-e-dimensionamento)
- [4. Duelo: Amazon EC2 vs. AWS Lambda](#4-duelo-amazon-ec2-vs-aws-lambda)
- [🎯 Gatilho de Exame](#-gatilho-de-exame)

---

## 1. O que é o AWS Lambda?

O **AWS Lambda** é um serviço de computação **Serverless** (sem servidor) que permite executar código sem que você precise provisionar, gerenciar ou aplicar patches em servidores, como instâncias EC2.

Você apenas faz o upload do seu código (Node.js, Python, Java, Go, .NET e outras linguagens suportadas) e a AWS cuida automaticamente da infraestrutura, disponibilidade, escalabilidade e gerenciamento do ambiente. Esse modelo é conhecido como **Function as a Service (FaaS)**, onde você se preocupa apenas com a lógica da aplicação.

---

## 2. Os Pilares do Modelo Serverless e do Lambda

Para a prova CLF-C02, existem três conceitos que praticamente aparecem em toda questão sobre Lambda.

### A. Escalabilidade Automática Instantânea (Automatic Scaling)

O Lambda escala praticamente **"de zero a herói"**. Se ninguém invocar sua função, nenhum recurso fica consumindo processamento. Agora imagine que, de repente, 10.000 usuários façam uma requisição ao mesmo tempo. A AWS cria automaticamente milhares de execuções paralelas para atender essa demanda e, quando tudo termina, libera esses recursos novamente. Você não configura Auto Scaling nem precisa criar servidores extras: toda essa elasticidade acontece de forma transparente.

### B. Modelo de Cobrança por Consumo Real (Pay-as-you-go)

Diferente do EC2, onde você paga pela instância ligada, no Lambda a cobrança acontece apenas quando sua função executa.

- **Requisições:** Você paga pelo número de chamadas da função.
- **Duração:** A cobrança considera o tempo de execução em milissegundos.
- **Ociosidade:** Se ninguém utilizar a função, o custo é praticamente **zero**.
- **Free Tier:** A AWS oferece **1 milhão de requisições gratuitas por mês**, benefício bastante citado em provas e documentações.

Esse modelo torna o Lambda extremamente econômico para aplicações que executam apenas sob demanda.

### C. Arquitetura Orientada a Eventos (Event-Driven)

O Lambda não fica executando continuamente esperando trabalho. Ele é um serviço **reativo**, que "acorda" somente quando algum evento acontece.

Os gatilhos mais comuns são:

- **Amazon S3:** Executar uma função sempre que um arquivo for enviado para um bucket (ex.: gerar thumbnails automaticamente).
- **Amazon DynamoDB:** Processar um evento quando um novo registro é criado ou alterado.
- **Amazon API Gateway:** Responder a requisições HTTP vindas de aplicações web ou mobile.

Na prática, qualquer serviço da AWS capaz de emitir eventos pode se tornar um gatilho para uma função Lambda.

---

## 3. Limitações Críticas e Dimensionamento

Nem tudo são flores. O Lambda foi projetado para tarefas rápidas (**short-lived**) e orientadas a eventos. Se sua aplicação precisa permanecer executando continuamente ou levar horas para concluir um processamento, provavelmente existe uma opção melhor.

Algumas limitações importantes para a prova:

- **15-minute execution timeout:** Nenhuma execução pode ultrapassar **15 minutos**. Se esse tempo for excedido, a AWS encerra automaticamente a função.
- **Memória:** Pode ser configurada entre **128 MB e 10 GB**, de acordo com a necessidade da aplicação.
- **CPU:** Você não escolhe diretamente a quantidade de vCPUs. A capacidade de processamento aumenta proporcionalmente à memória configurada. Em outras palavras, aumentar a memória também aumenta o poder de processamento disponível.

---

## 4. Duelo: Amazon EC2 vs. AWS Lambda

| Característica | Amazon EC2 | AWS Lambda |
| :--- | :--- | :--- |
| **Gerenciamento** | Você administra SO, patches e segurança. | **Zero server management** (AWS cuida da infraestrutura). |
| **Execução** | Contínua, enquanto a instância estiver ligada. | Sob demanda, apenas quando um evento ocorre. |
| **Escalabilidade** | Manual ou via Auto Scaling Group. | **Automática e transparente**. |
| **Cobrança** | Tempo em que a instância permanece ligada. | Requisições + tempo de execução. |
| **Uso Ideal** | Aplicações persistentes, legadas ou de longa duração. | Microsserviços, automações e aplicações orientadas a eventos. |

---

## 🎯 Gatilho de Exame

Se aparecer qualquer um destes termos, o pensamento deve ir imediatamente para **AWS Lambda**:

- **AWS Lambda:** Serviço serverless para execução de funções.
- **Serverless computing:** Computação sem gerenciamento de servidores.
- **Function as a Service (FaaS):** Execução de código sob demanda.
- **Event-driven architecture:** Código disparado por eventos (S3, SNS, DynamoDB, API Gateway).
- **Pay-as-you-go pricing model:** Cobrança baseada apenas em requisições e tempo de execução.
- **Automatic scaling:** Escalonamento automático realizado pela AWS.
- **Zero server management:** Toda a infraestrutura fica sob responsabilidade da AWS.
- **15-minute execution timeout:** Tempo máximo permitido para uma execução.

> **💡 Sinal de Alerta:** Se a questão mencionar uma aplicação que precisa ficar executando continuamente ou um processamento que leva mais de **15 minutos**, descarte o Lambda. Nesses cenários, normalmente a resposta será **Amazon EC2** ou **AWS Batch**, dependendo do tipo de carga de trabalho.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 3: ELB e Auto Scaling - O Combo da Alta Disponibilidade](02-auto-scaling-e-elastic-load-balancing.md)
* [➡️ Módulo 3: Contêineres na AWS - ECS, EKS e a Revolução Fargate](04-containers-ecs-fargate-e-eks-kubernetes.md)

---
---