# Mnemônicos e Atalhos: O Guia de Sobrevivência da CLF-C02

A CLF-C02 não é difícil porque os serviços são complexos; ela é difícil porque muitos parecem fazer a mesma coisa. Este guia reúne os principais mnemônicos e atalhos para você eliminar alternativas rapidamente e chegar ao gabarito sem perder tempo.

---

## 1. Mnemônicos de Ouro

### Opções de Compra EC2

* **On-Demand:** Pense em um **Airbnb**. Usa quando precisa, paga pelo tempo utilizado e pode sair quando quiser. **Foco:** Flexibilidade.
* **Reserved / Savings Plans:** Pense em um **contrato de aluguel**. Você assume um compromisso de 1 ou 3 anos e recebe um grande desconto. **Foco:** Economia para cargas estáveis.
* **Spot:** Pense em um **leilão**. Muito barato, mas pode ser interrompido a qualquer momento. **Foco:** Workloads tolerantes a falhas.

### EC2 vs. Lambda

* **EC2:** Você administra o servidor (SO, patches, escalabilidade e manutenção).
* **Lambda:** Você entrega apenas o código. A AWS gerencia toda a infraestrutura.

> **Regra dos 15:** Se a execução durar mais de **15 minutos**, descarte o Lambda.

### Load Balancers

* **ALB (Application):** Camada 7. Entende HTTP/HTTPS e roteia por URL ou Host.
* **NLB (Network):** Camada 4. Alta performance, TCP/UDP, baixa latência e suporte a IP estático.

### Containers

* **ECS:** Orquestrador nativo da AWS.
* **EKS:** Kubernetes gerenciado.
* **Fargate:** Contêineres sem gerenciar instâncias EC2.

---

## 2. Pegadinhas Clássicas da Prova

A banca costuma repetir alguns padrões de distração:

* **Banco de dados + menor custo:** Não escolha **Spot**. Bancos de dados exigem disponibilidade. A resposta costuma ser **Reserved Instances** ou **Savings Plans**.
* **Processamento longo (40 min, 1 hora...):** Não escolha **Lambda**. O limite é 15 minutos. Pense em **AWS Batch** ou **Amazon EC2**.
* **Menor esforço operacional:** Evite alternativas que exigem administrar servidores. Procure por **Lambda**, **Fargate** ou **Elastic Beanstalk**.

---

## 3. Cheat Sheet

| Se o enunciado falar em... | Pense imediatamente em... |
| :--- | :--- |
| Serverless + eventos | **AWS Lambda** |
| WordPress simples | **Amazon Lightsail** |
| Kubernetes | **Amazon EKS** |
| Contêiner sem EC2 | **AWS Fargate** |
| HTTP/HTTPS ou URL | **Application Load Balancer (ALB)** |
| TCP/UDP, IP estático ou baixa latência | **Network Load Balancer (NLB)** |
| Economia para workload estável | **Savings Plans / Reserved Instances** |
| Economia máxima com interrupção | **Spot Instances** |
| Processamento em lote | **AWS Batch** |

---

## 🎯 Gatilho de Exame

Sempre associe estes termos ao serviço correto:

* **Serverless:** Lambda ou Fargate.
* **Event-driven:** Lambda.
* **Managed Kubernetes:** Amazon EKS.
* **Container orchestration:** Amazon ECS ou Amazon EKS.
* **Path-based routing:** Application Load Balancer.
* **Static IP / TCP / UDP:** Network Load Balancer.
* **Predictable monthly pricing:** Amazon Lightsail.
* **Batch computing workloads:** AWS Batch.
* **Fault-tolerant workloads:** Spot Instances.
* **Steady-state workloads:** Reserved Instances ou Savings Plans.

> **Sinal de Alerta:** A banca normalmente descreve o problema, não o serviço. Primeiro identifique o requisito principal (serverless, menor esforço operacional, alta performance, processamento em lote ou economia) e só depois escolha a alternativa. Esse raciocínio elimina a maior parte das pegadinhas.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 3: Comparativo de Famílias EC2 - A Máquina Certa para o Job](06-tabela-comparativa-familias-instancia-ec2.md)
* [➡️ Módulo 3: Lab - Lançando Instância EC2 com User Data](08-lab-lancando-instancia-ec2-com-userdata.md)

---
---