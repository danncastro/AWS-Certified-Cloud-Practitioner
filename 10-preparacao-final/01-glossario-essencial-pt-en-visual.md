# Glossário Essencial PT-EN: O Dicionário de Guerra da CLF-C02

A AWS fala inglês. Mesmo que você faça a prova em português, praticamente todos os nomes dos serviços e boa parte dos termos técnicos aparecem em inglês.

Isso significa que, se você travar ao ler palavras como **Elasticity**, **Fault Tolerance** ou **Shared Responsibility Model**, vai desperdiçar tempo precioso durante a prova.

A ideia deste glossário é simples: transformar os principais termos da CLF-C02 em associações rápidas para que, ao bater o olho no enunciado, você identifique imediatamente o conceito que a banca está cobrando.

---

# 1. Conceitos de Nuvem e Arquitetura

| Termo (PT) | Termo (EN) | Sigla | Definição para a CLF-C02 |
| :--- | :--- | :---: | :--- |
| **Alta Disponibilidade** | High Availability | **HA** | Mantém a aplicação disponível mesmo quando um componente falha, normalmente utilizando múltiplas Availability Zones. |
| **Tolerância a Falhas** | Fault Tolerance | — | Capacidade de continuar operando mesmo durante uma falha, sem interrupção perceptível do serviço. |
| **Elasticidade** | Elasticity | — | Ajusta automaticamente os recursos conforme a demanda aumenta ou diminui. |
| **Escalabilidade** | Scalability | — | Capacidade de crescer para suportar mais carga de trabalho mantendo o desempenho. |
| **Agilidade** | Agility | — | Provisionamento rápido de recursos, reduzindo o tempo entre a ideia e a implantação. |
| **Economia de Escala** | Economies of Scale | — | A AWS consegue oferecer preços menores graças à sua enorme infraestrutura global. |
| **Pagamento por Uso** | Pay-as-you-go | — | Você paga apenas pelos recursos efetivamente consumidos. |

---

# 2. Computação e Containers

| Termo (PT) | Termo (EN) | Sigla | Definição para a CLF-C02 |
| :--- | :--- | :---: | :--- |
| **Nuvem Computacional Elástica** | Elastic Compute Cloud | **EC2** | Serviço de máquinas virtuais (IaaS), onde você administra sistema operacional e aplicações. |
| **Sem Servidor** | Serverless | — | Modelo em que a AWS gerencia toda a infraestrutura e você se preocupa apenas com o código ou a aplicação. |
| **Função como Serviço** | Function as a Service | **AWS Lambda** | Executa código sob demanda, acionado por eventos, sem gerenciamento de servidores. |
| **Orquestração de Containers** | Container Orchestration | **ECS / EKS** | Serviços para executar e administrar aplicações em containers. O ECS é nativo da AWS; o EKS utiliza Kubernetes. |
| **Computação Serverless para Containers** | Serverless Compute for Containers | **AWS Fargate** | Executa containers sem provisionar ou administrar instâncias EC2. |

> **Pegadinha frequente:** Se o enunciado disser **"não quero gerenciar servidores"**, normalmente a resposta será **Lambda** ou **Fargate**.

---

# 3. Armazenamento e Banco de Dados

| Termo (PT) | Termo (EN) | Sigla | Definição para a CLF-C02 |
| :--- | :--- | :---: | :--- |
| **Armazenamento de Objetos** | Object Storage | **Amazon S3** | Armazena arquivos por meio de objetos. Muito usado para backups, data lakes e hospedagem de sites estáticos. |
| **Armazenamento em Blocos** | Block Storage | **Amazon EBS** | Disco virtual utilizado por instâncias EC2 dentro de uma Availability Zone. |
| **Sistema de Arquivos em Rede** | Network File System | **Amazon EFS** | Sistema de arquivos compartilhado que pode ser acessado simultaneamente por várias instâncias Linux. |
| **Banco de Dados Relacional** | Relational Database | **Amazon RDS** | Serviço gerenciado para bancos SQL como MySQL, PostgreSQL, Oracle e SQL Server. |
| **Banco de Dados Não Relacional** | NoSQL Database | **Amazon DynamoDB** | Banco NoSQL serverless de chave-valor e documentos com baixa latência. |
| **Armazém de Dados** | Data Warehouse | **Amazon Redshift** | Banco otimizado para análises massivas (OLAP) e Business Intelligence. |

---

# 4. Redes, Segurança e Identidade

| Termo (PT) | Termo (EN) | Sigla | Definição para a CLF-C02 |
| :--- | :--- | :---: | :--- |
| **Nuvem Privada Virtual** | Virtual Private Cloud | **VPC** | Rede virtual isolada onde você define IPs, sub-redes e regras de comunicação. |
| **Ponto de Presença** | Point of Presence | **Edge Location** | Infraestrutura utilizada por serviços como CloudFront para reduzir latência e aproximar o conteúdo dos usuários. |
| **Menor Privilégio** | Least Privilege | — | Conceda apenas as permissões necessárias para executar uma determinada tarefa. |
| **Autenticação Multifator** | Multi-Factor Authentication | **MFA** | Camada adicional de autenticação além da senha. |
| **Trilha de Auditoria** | Audit Trail | **AWS CloudTrail** | Histórico das chamadas de API realizadas na conta AWS. |
| **Criptografia em Repouso** | Encryption at Rest | — | Dados protegidos enquanto permanecem armazenados em disco. |

---

# ⚡ Pares de Confusão (Não Caia Nessa!)

Essa seção existe porque a AWS adora colocar alternativas muito parecidas na prova.

## Availability Zone × Region

| Region | Availability Zone |
| :--- | :--- |
| Área geográfica da AWS. | Data center (ou conjunto de data centers) isolado dentro de uma Region. |
| Exemplo: São Paulo (`sa-east-1`). | Exemplo: `sa-east-1a`, `sa-east-1b`. |

**Resumo mental:**

- **Region** → localização geográfica.
- **AZ** → disponibilidade física.

---

## Rehost × Refactor

| Rehost | Refactor |
| :--- | :--- |
| Migra praticamente sem alterar o código ("Lift and Shift"). | Reescreve ou adapta a aplicação para aproveitar recursos Cloud Native. |

---

## AWS Pricing Calculator × AWS Cost Explorer

| Pricing Calculator | Cost Explorer |
| :--- | :--- |
| Estima custos antes da implantação. | Analisa custos reais após o uso dos recursos. |

---

## Amazon SQS × Amazon SNS

| Amazon SQS | Amazon SNS |
| :--- | :--- |
| Serviço de filas de mensagens. | Serviço de notificações Pub/Sub. |
| A mensagem permanece na fila até ser consumida. | A mensagem é distribuída imediatamente aos assinantes. |

---

## Security Group × Network ACL

| Security Group | Network ACL |
| :--- | :--- |
| Atua na instância. | Atua na sub-rede. |
| Stateful. | Stateless. |
| Permite apenas regras de Allow. | Permite regras de Allow e Deny. |

> **Essa é uma das pegadinhas favoritas da prova.**

---

# 🎯 Gatilho de Exame

Associe rapidamente o termo ao serviço correspondente:

- **Less Operational Effort** → Serviços Gerenciados ou Serverless
- **Managed Service** → A AWS administra a infraestrutura
- **On-premises Integration** → AWS Storage Gateway, AWS Direct Connect ou Site-to-Site VPN
- **Global Reach** → Amazon CloudFront ou AWS Global Accelerator
- **Low Latency** → CloudFront, Route 53 ou Global Accelerator
- **Audit** → AWS CloudTrail
- **Compliance Reports** → AWS Artifact
- **Configuration History** → AWS Config
- **Predictable Pricing** → Amazon Lightsail ou Reserved Instances
- **Pay only for what you use** → Modelo Pay-as-you-go

---

> ## 💡 Dica de Ouro
>
> A AWS costuma repetir determinados verbos nos enunciados. Aprender essas associações acelera muito a identificação da resposta correta.
>
> - **Distribute** → Load Balancer
> - **Scale** → Auto Scaling
> - **Route** → Route 53
> - **Monitor** → Amazon CloudWatch
> - **Audit** → AWS CloudTrail
> - **Encrypt** → AWS KMS
> - **Protect** → AWS Shield ou AWS WAF (dependendo do contexto)
>
> Quanto mais rápido você associar essas palavras aos serviços, mais tempo sobrará para analisar as questões realmente difíceis. Marcha!

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 10: Cronograma Acelerado - Aprovação em 30 Dias (CLF-C02)](00-cronograma-acelerado-30-dias.md)
* [➡️ Módulo 10: Simulado Completo CLF-C02 - Versão 1 - Reta Final](02-simulado-completo-v1-blueprint-real.md)

---