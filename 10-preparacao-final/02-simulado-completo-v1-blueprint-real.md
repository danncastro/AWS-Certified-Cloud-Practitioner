# Simulado Completo CLF-C02: Versão 1 - Reta Final

Chegou a hora da verdade. Estudar teoria é base, mas passar na prova é sobre entender como a AWS faz as perguntas e não cair nas cascas de banana da banca. Este simulado foi montado seguindo o peso real do blueprint da CLF-C02. Trate isso aqui como o "dia D". Cronometra seu tempo, elimina as absurdas e foca nos gatilhos técnicos.

---

## Questões

### 1. Uma startup deseja lançar uma nova aplicação e quer evitar o investimento inicial pesado em hardware físico, preferindo pagar apenas pelos recursos que consumir mensalmente. Qual conceito da economia da nuvem descreve essa mudança?
A) Mudança de Operational Expenditure (OpEx) para Capital Expenditure (CapEx).
B) Mudança de Capital Expenditure (CapEx) para Operational Expenditure (OpEx).
C) Implementação de High Availability para redução de custos fixos.
D) Uso de instâncias Dedicated Hosts para maximizar o retorno de investimento.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B**
> * **Por que está certa:** A nuvem permite trocar despesas de capital (CapEx - investimento alto em ativos físicos) por despesas operacionais (OpEx - custos recorrentes por uso).
> * **Distratores:** A (é o inverso), C (disponibilidade não define modelo contábil), D (Dedicated Hosts aumentam o custo e gestão).

</details>

---

### 2. Um arquiteto de soluções está projetando uma aplicação que precisa ser resiliente a falhas de um data center inteiro dentro de uma única região. Qual estratégia de infraestrutura global da AWS deve ser utilizada?
A) Implantar a aplicação em múltiplos Edge Locations.
B) Usar o AWS Global Accelerator para rotear o tráfego.
C) Implantar a aplicação em múltiplas Availability Zones (AZs).
D) Configurar o S3 Transfer Acceleration para replicação de dados.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C**
> * **Por que está certa:** Availability Zones são data centers isolados dentro de uma região. Se um cai, os outros seguram a onda.
> * **Distratores:** A (Edge Locations são para cache, não host de app resiliente), B (Accelerator otimiza rota, não evita falha de AZ), D (Transfer Acceleration é para upload no S3).

</details>

---

### 3. De acordo com o Modelo de Responsabilidade Compartilhada da AWS, qual das seguintes tarefas é de responsabilidade exclusiva do cliente ao utilizar o Amazon EC2?
A) Manutenção física dos servidores e do hardware de rede.
B) Gerenciamento da camada do hipervisor.
C) Aplicação de patches de segurança no sistema operacional convidado (Guest OS).
D) Descarte seguro de dispositivos de armazenamento de dados antigos.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C**
> * **Por que está certa:** No modelo IaaS (EC2), a AWS cuida do hardware e hipervisor. O cliente é dono de tudo que roda dentro da instância, incluindo o SO.
> * **Distratores:** A, B e D são responsabilidades da AWS (Security OF the cloud).

</details>

---

### 4. Uma empresa precisa garantir que seus desenvolvedores tenham apenas as permissões estritamente necessárias para realizar suas tarefas, sem acesso a recursos financeiros ou de segurança crítica. Qual princípio de segurança do IAM está sendo aplicado?
A) Multi-Factor Authentication (MFA).
B) Principle of Least Privilege.
C) Shared Responsibility Model.
D) Role-based Access Control com acesso root.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B**
> * **Por que está certa:** O Principle of Least Privilege dita que você deve dar apenas o acesso mínimo necessário para o trabalho ser feito.
> * **Distratores:** A (MFA é autenticação), C (é um modelo de divisão de tarefas), D (acesso root é o oposto de privilégio mínimo).

</details>

---

### 5. Qual serviço da AWS permite que um cliente baixe relatórios de conformidade (como SOC 1, SOC 2 e PCI) e aceite acordos de segurança diretamente pelo console?
A) AWS Artifact.
B) AWS Trusted Advisor.
C) AWS Shield.
D) Amazon GuardDuty.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: A**
> * **Por que está certa:** O AWS Artifact é o portal oficial de documentos de compliance.
> * **Distratores:** B (dá dicas de melhoria), C (protege contra DDoS), D (detecta ameaças/invasões).

</details>

---

### 6. Uma aplicação web apresenta picos de tráfego imprevisíveis durante o dia. Qual característica da nuvem AWS permite que a infraestrutura aumente ou diminua a capacidade automaticamente para atender a essa demanda variável?
A) Scalability.
B) Reliability.
C) Elasticity.
D) Agility.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C**
> * **Por que está certa:** Elasticidade é a capacidade de aumentar (scale out) ou diminuir (scale in) recursos automaticamente conforme a demanda oscila.
> * **Distratores:** A (capacidade de crescer de forma sustentada), B (capacidade de manter o serviço no ar), D (velocidade de lançamento).

</details>

---

### 7. Uma instituição financeira precisa armazenar registros de transações por 7 anos para cumprir requisitos regulatórios. Os dados raramente são acessados, e um tempo de recuperação de 12 a 48 horas é aceitável. Qual a classe de armazenamento do Amazon S3 mais econômica para este caso?
A) S3 Standard-Infrequent Access.
B) S3 Intelligent-Tiering.
C) S3 Glacier Flexible Retrieval.
D) S3 Glacier Deep Archive.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: D**
> * **Por que está certa:** Deep Archive é a classe mais barata para dados acessados 1-2 vezes ao ano e com tempos de espera de horas.
> * **Distratores:** A (mais cara que Glacier), B (para padrões desconhecidos), C (Glacier "comum", mais cara que a Deep Archive).

</details>

---

### 8. Qual serviço de banco de dados NoSQL da AWS é totalmente gerenciado, serverless e oferece latência de milissegundo de dígito único para aplicações em escala global?
A) Amazon RDS.
B) Amazon Aurora.
C) Amazon DynamoDB.
D) Amazon Redshift.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C**
> * **Por que está certa:** DynamoDB é o banco NoSQL serverless padrão da AWS para performance massiva.
> * **Distratores:** A (relacional), B (relacional de alta performance), D (data warehouse para análise).

</details>

---

### 9. Um gestor financeiro quer receber uma notificação automática por e-mail sempre que os custos mensais da conta ultrapassarem a marca de $500. Qual ferramenta deve ser configurada?
A) AWS Cost Explorer.
B) AWS Budgets.
C) AWS Pricing Calculator.
D) AWS Cost Anomaly Detection.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B**
> * **Por que está certa:** AWS Budgets permite criar orçamentos e alertas (alarmes) baseados em limites de custo ou uso.
> * **Distratores:** A (analisa gastos passados), C (estima antes de gastar), D (caça surpresas por anomalia).

</details>

---

### 10. Para desacoplar os componentes de uma arquitetura de microserviços e garantir que a falha de um componente não derrube o sistema inteiro, qual par de serviços é mais indicado para mensageria e eventos?
A) Amazon SQS e Amazon SNS.
B) Amazon EC2 e Amazon EBS.
C) AWS Lambda e AWS Step Functions.
D) Amazon CloudFront e AWS WAF.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: A**
> * **Por que está certa:** SQS (filas) e SNS (notificações) são os pilares para desacoplamento de microserviços.
> * **Distratores:** B (servidor e disco), C (computação e orquestração de fluxo), D (entrega e firewall).

</details>

---

### 11. Qual recurso da VPC atua como um firewall stateful no nível da instância EC2 para filtrar o tráfego de entrada e saída?
A) Network ACL (NACL).
B) Internet Gateway (IGW).
C) Security Group.
D) NAT Gateway.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C**
> * **Por que está certa:** Security Groups são firewalls de nível de instância e são stateful (ele lembra que você pediu a conexão e deixa a resposta entrar).
> * **Distratores:** A (nível de subnet e stateless), B (conecta VPC à internet), D (saída de internet para redes privadas).

</details>

---

### 12. Uma empresa com plano de suporte Enterprise deseja obter orientação arquitetônica contínua e revisões de infraestrutura proativas por um especialista da AWS designado para sua conta. Quem é esse profissional?
A) AWS Support Concierge.
B) AWS Solutions Architect (SA).
C) Technical Account Manager (TAM).
D) Cloud Support Engineer.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C**
> * **Por que está certa:** O TAM é o contato técnico dedicado exclusivo dos planos Enterprise e Enterprise On-Ramp.
> * **Distratores:** A (ajuda com faturamento/conta), B (cargo geral da AWS, não necessariamente um contato designado fixo), D (resolve chamados técnicos específicos).

</details>

---

### 13. Qual pilar do AWS Well-Architected Framework foca na capacidade de uma carga de trabalho executar suas funções pretendidas e se recuperar rapidamente de falhas de infraestrutura ou serviço?
A) Operational Excellence.
B) Security.
C) Reliability.
D) Performance Efficiency.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C**
> * **Por que está certa:** Confiabilidade (Reliability) é o pilar focado em resiliência e recuperação de desastres.
> * **Distratores:** A (focado em processos/automação), B (proteção de dados), D (uso eficiente de recursos).

</details>

---

### 14. Uma empresa decide migrar seu data center local para a AWS realizando o famoso "Lift and Shift", movendo os servidores como estão, sem alterações no código. Qual estratégia de migração do Cloud Adoption Framework (CAF) está sendo usada?
A) Replatform.
B) Rehost.
C) Refactor.
D) Repurchase.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B**
> * **Por que está certa:** Rehost (Lift and Shift) é mover para a nuvem sem alterar a aplicação.
> * **Distratores:** A (faz pequenos ajustes no SO/Config), C (reescreve o código para ser cloud-native), D (troca por um software SaaS).

</details>

---

### 15. Qual recurso do AWS Organizations permite que o administrador da conta master restrinja quais serviços e ações podem ser executados pelos usuários e roles dentro das contas membro da organização?
A) IAM User Policies.
B) Service Control Policies (SCPs).
C) Resource-based Policies.
D) AWS Config Rules.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B**
> * **Por que está certa:** Service Control Policies (SCPs) definem o teto máximo de permissões em uma organização.
> * **Distratores:** A (aplica-se a usuários/roles individuais), C (anexadas a recursos como buckets), D (auditores de conformidade).

</details>

---

### 16. Um desenvolvedor quer executar um script de processamento de dados que dura apenas 30 segundos, disparado por um upload no S3, sem precisar gerenciar servidores. Qual serviço de computação é o ideal?
A) Amazon EC2.
B) AWS Lambda.
C) Amazon ECS.
D) AWS Fargate.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B**
> * **Por que está certa:** AWS Lambda executa código curto orientado a eventos sem gerenciar nenhuma infraestrutura (Serverless).
> * **Distratores:** A (IaaS pura), C e D (Containers, exigem mais configuração que o Lambda aqui).

</details>

---

### 17. Qual serviço da AWS funciona como uma Content Delivery Network (CDN) para entregar conteúdo com baixa latência e alta velocidade de transferência através de Edge Locations?
A) Amazon Route 53.
B) Amazon CloudFront.
C) AWS Global Accelerator.
D) Amazon VPC Peering.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B**
> * **Por que está certa:** CloudFront é a CDN da AWS integrada com Edge Locations globais.
> * **Distratores:** A (DNS), C (acelera protocolo TCP/UDP via IP fixo), D (conecta duas VPCs).

</details>

---

### 18. Uma empresa quer proteger seu banco de dados contra exclusão acidental e possibilitar o Point-in-Time Restore (PITR). Qual recurso do Amazon RDS deve ser garantido?
A) Read Replicas.
B) Multi-AZ Deployment.
C) Automated Backups.
D) DB Snapshots manuais apenas.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C**
> * **Por que está certa:** Automated Backups no RDS permitem restaurar o banco para qualquer segundo dentro da janela de retenção.
> * **Distratores:** A (escala leitura), B (alta disponibilidade), D (fotos manuais que não permitem restauração por segundo específica).

</details>

---

### 19. Qual ferramenta da AWS fornece recomendações automáticas para otimizar custos, aumentar a segurança e melhorar a performance, baseada na análise de uso da conta em 5 categorias?
A) AWS Trusted Advisor.
B) AWS Inspector.
C) Amazon CloudWatch.
D) AWS Compute Optimizer.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: A**
> * **Por que está certa:** Trusted Advisor analisa a conta e dá recomendações em 5 categorias (Custo, Segurança, Performance, Tolerância a Falhas e Service Limits).
> * **Distratores:** B (scaneia vulnerabilidades em instâncias), C (monitora métricas), D (focado apenas em dimensionamento de computação).

</details>

---

### 20. De acordo com o Modelo de Responsabilidade Compartilhada, quem é responsável pela segurança física dos data centers onde a infraestrutura da AWS reside?
A) O cliente.
B) A AWS.
C) Ambos (responsabilidade compartilhada).
D) O provedor de internet local.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B**
> * **Por que está certa:** Segurança física, hardware e redes globais são responsabilidade da AWS (Security OF the cloud).
> * **Distratores:** A (cuida do que está NA nuvem), C e D (estão erradas conforme o modelo oficial).

</details>

---

## 🎯 Gatilho de Exame

Para amassar na prova, você precisa dessas táticas:

1.  **Eliminação por Escopo:** Se a questão fala em "Site WordPress barato" e houver **Amazon Lightsail**, pare de ler e marque. Se fala em "Processamento em lote massivo", vá de **AWS Batch**.
2.  **Palavras-Chave de Serviço:**
    *   *Auditoria:* CloudTrail.
    *   *Governança de Configuração:* AWS Config.
    *   *Escalar Horizontalmente:* Auto Scaling.
    *   *IP Fixo / Latência Extrema:* Network Load Balancer (NLB).
    *   *Roteamento por URL:* Application Load Balancer (ALB).
3.  **Gestão de Tempo:** Você tem cerca de 1.3 minutos por questão. Se a pergunta for um texto gigante, pule para a última frase (o comando da questão) e olhe as alternativas. Geralmente, o contexto inicial é só "fluff".
4.  **Mentalidade de "Menor Esforço":** A AWS sempre valoriza a resposta que remove o peso operacional das suas costas. Se uma alternativa diz "Configurar um script manual no cron do Linux" e a outra diz "Usar AWS Lambda", a Lambda quase sempre é o gabarito.

---

> **Sinal de Alerta:**
> 
> - **CapEx vs OpEx** ➔ Nuvem é OpEx (pague pelo que usa), Data Center tradicional é CapEx (investimento físico alto).
> - **Stateful vs Stateless** ➔ Security Groups são stateful (lembram do tráfego de ida), NACLs são stateless (precisam de regras explícitas para ida e volta).
> - **Trusted Advisor vs Inspector** ➔ Trusted Advisor olha a conta como um todo (custo, segurança geral, performance), enquanto o Inspector foca em vulnerabilidades de instâncias e imagens de container.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 10: Glossário Essencial PT-EN - O Dicionário de Guerra da CLF-C02](01-glossario-essencial-pt-en-visual.md)
* [➡️ Módulo 10: Simulado Completo CLF-C02: Versão 2 - O Teste Final](03-simulado-completo-v2-blueprint-real.md)

---