# 📝 Micro-Simulado: Computação e Containers

Computação é um dos pilares mais importantes da prova **AWS Certified Cloud Practitioner (CLF-C02)**.

A banca não espera que você saiba criar um cluster Kubernetes do zero ou administrar servidores em produção, mas ela quer saber se você entende **qual serviço resolve cada problema de negócio**.

A grande armadilha desse domínio é confundir serviços parecidos:

- EC2 vs Lambda.
- ECS vs Fargate.
- Spot vs Reserved.
- ALB vs NLB.
- Escalabilidade vs Gerenciamento operacional.

Bora validar se esses conceitos ficaram sólidos.

---

## Questões

**1. Uma empresa de análise de dados precisa processar grandes volumes de informações em um workload que pode ser interrompido e retomado a qualquer momento. O objetivo principal é reduzir os custos ao máximo.**

**Qual opção de compra do Amazon EC2 é a mais indicada?**

- A) On-Demand Instances.
- B) Reserved Instances.
- C) Spot Instances.
- D) Dedicated Hosts.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C (Spot Instances)**
>
> * **Por que é a certa:** Spot Instances utilizam capacidade ociosa da AWS e podem oferecer descontos de até 90%. São indicadas para workloads tolerantes a interrupções.
> * **A pegadinha:** O ponto-chave do enunciado é "pode ser interrompido". Quando existe tolerância à falha e prioridade em custo, pense em Spot.
>
> * **A) On-Demand:** Flexível, mas possui custo maior.
> * **B) Reserved:** Boa opção para workloads previsíveis, porém exige compromisso de uso.
> * **D) Dedicated Hosts:** Usado para requisitos específicos de isolamento, licenciamento ou compliance.

</details>

---

**2. Um desenvolvedor precisa executar um processamento de imagens sempre que um arquivo é enviado para um bucket Amazon S3. O processamento leva cerca de 5 minutos e a empresa não quer gerenciar servidores nem pagar por recursos ociosos.**

**Qual serviço deve ser utilizado?**

- A) Amazon EC2.
- B) AWS Lambda.
- C) AWS Batch.
- D) Amazon Lightsail.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B (AWS Lambda)**
>
> * **Por que é a certa:** Lambda executa código sob demanda, escala automaticamente e cobra apenas pelo tempo de execução utilizado.
> * **A pegadinha:** A frase "não quer gerenciar servidores" indica uma solução serverless.
>
> * **A) EC2:** Exige gerenciamento de servidores, sistema operacional e capacidade.
> * **C) AWS Batch:** Indicado para processamento batch de larga escala.
> * **D) Lightsail:** Simplifica servidores virtuais, mas não executa funções event-driven.

</details>

---

**3. Uma aplicação utiliza um banco de dados em memória (in-memory database) e precisa de grandes quantidades de RAM.**

**Qual família de instâncias EC2 deve ser utilizada?**

- A) Compute Optimized (C).
- B) Memory Optimized (R).
- C) Storage Optimized (I).
- D) General Purpose (M).

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B (Memory Optimized - R)**
>
> * **Por que é a certa:** Instâncias Memory Optimized são projetadas para aplicações que precisam trabalhar com grandes volumes de memória RAM, como bancos em memória.
> * **A pegadinha:** O recurso principal citado é memória, não CPU ou armazenamento.
>
> * **A) Compute Optimized:** Melhor para cargas intensivas de processamento.
> * **C) Storage Optimized:** Focada em alto desempenho de armazenamento e IOPS.
> * **D) General Purpose:** Equilíbrio entre CPU, memória e rede.

</details>

---

**4. Para garantir alta disponibilidade de uma aplicação web, qual arquitetura representa a melhor prática?**

- A) EC2 em uma única Availability Zone.
- B) Application Load Balancer distribuindo tráfego para um Auto Scaling Group em múltiplas Availability Zones.
- C) AWS Lambda conectado a instâncias Spot.
- D) Amazon CloudFront apontando para um único servidor on-premises.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B (ALB + Auto Scaling Group em múltiplas AZs)**
>
> * **Por que é a certa:** O Application Load Balancer distribui requisições entre múltiplas instâncias saudáveis, enquanto o Auto Scaling Group substitui instâncias com falha automaticamente.
> * **A pegadinha:** Alta disponibilidade exige eliminar pontos únicos de falha.
>
> * **A) Uma única AZ:** Possui risco de indisponibilidade.
> * **C) Lambda + Spot:** São serviços válidos em outros cenários, mas não representam essa arquitetura clássica.
> * **D) CloudFront:** Reduz latência, mas não resolve uma origem única.

</details>

---

**5. Uma empresa deseja executar contêineres Docker sem provisionar ou administrar instâncias EC2.**

**Qual serviço atende esse requisito?**

- A) Amazon ECS com EC2 Launch Type.
- B) Amazon EKS com instâncias Spot.
- C) AWS Fargate.
- D) Amazon Lightsail Containers.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C (AWS Fargate)**
>
> * **Por que é a certa:** O AWS Fargate permite executar contêineres sem precisar gerenciar servidores ou clusters de máquinas.
> * **A pegadinha:** A palavra-chave é "sem provisionar ou administrar instâncias EC2".
>
> * **A) ECS EC2 Launch Type:** Ainda exige gerenciamento das instâncias.
> * **B) EKS com Spot:** Kubernetes continua exigindo gerenciamento dos nós.
> * **D) Lightsail Containers:** É uma solução simplificada, mas não é o serviço padrão para esse cenário.

</details>

---

# 🎯 Gatilho de Exame

Associe rapidamente o problema à solução:

- **Workload interrompível / menor custo possível** ➔ **Spot Instances**
- **Execução de código sob demanda** ➔ **AWS Lambda**
- **Sem gerenciamento de servidores para containers** ➔ **AWS Fargate**
- **Grande quantidade de memória RAM** ➔ **Memory Optimized EC2**
- **Escalar automaticamente instâncias** ➔ **Auto Scaling Group**
- **Distribuir tráfego HTTP/HTTPS** ➔ **Application Load Balancer (ALB)**
- **Alta performance TCP/UDP e IP fixo** ➔ **Network Load Balancer (NLB)**
- **Preço previsível e simples para aplicações pequenas** ➔ **Amazon Lightsail**

---

> **Sinal de Alerta:**  
> Se o enunciado mencionar:
>
> - **"Não quero gerenciar servidores"** → pense em **Lambda ou Fargate**.
> - **"Pode ser interrompido"** → pense em **Spot Instances**.
> - **"Grande quantidade de memória"** → pense em **Memory Optimized**.
> - **"Alta disponibilidade"** → pense em **Load Balancer + Auto Scaling + Multi-AZ**.
> - **"Processamento por evento"** → pense em **Lambda**.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 3: Lab - Lançando Instância EC2 com User Data](08-lab-lancando-instancia-ec2-com-userdata.md)
* [➡️ Módulo 4: Amazon S3 - Armazenamento de Objetos e API](../04-armazenamento-e-transferencia/00-s3-armazenamento-de-objetos-api.md)

---
---