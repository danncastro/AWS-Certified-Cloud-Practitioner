# Simulado Completo CLF-C02: Versão 2 - O Teste Final

Se você chegou aqui, já passou pela teoria e pelo primeiro simulado. Agora o buraco é mais embaixo. A banca da AWS adora cenários onde duas opções parecem certas, mas apenas uma é a "AWS Way" (mais gerenciada, mais barata ou mais resiliente). Este simulado foca nessas nuances e nos serviços que costumam confundir a galera na reta final.

Prepare o cronômetro, esqueça o Google e foque no requisito dominante de cada questão.

---

## Questões

### 1. Uma empresa de mídia precisa migrar 150 TB de dados históricos para o Amazon S3. A conexão de internet local é instável e levaria meses para concluir o upload. Qual solução oferece o menor esforço e maior velocidade para essa transferência offline?
- A) AWS DataSync.
- B) AWS Snowball Edge Storage Optimized.
- C) S3 Transfer Acceleration.
- D) Amazon VPC Peering.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B**
> * **Por que está certa:** O Snowball Edge é um dispositivo físico para migração offline de grandes volumes (terabytes a petabytes), ideal para conexões instáveis ou lentas.
> * **Distratores:** A (DataSync é online), C (Acceleration é para upload online via Edge Locations), D (VPC Peering conecta redes na AWS).

</details>

---

### 2. De acordo com o Modelo de Responsabilidade Compartilhada da AWS, qual das seguintes ações é uma responsabilidade exclusiva do cliente ao gerenciar o Amazon RDS?
- A) Realizar o gerenciamento de patches do sistema operacional subjacente.
- B) Gerenciar a segurança física das instalações de armazenamento de dados.
- C) Configurar permissões de acesso e criptografia de dados em repouso.
- D) Substituir hardware de computação ou unidades de disco com falha.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C**
> * **Por que está certa:** No RDS (PaaS), a AWS cuida do hardware e do SO. O cliente é responsável por tudo que acontece dentro do banco de dados (acesso, criptografia, configuração de esquema).
> * **Distratores:** A, B e D são responsabilidades da AWS ("Security OF the cloud").

</details>

---

### 3. Um arquiteto de soluções deseja garantir que os usuários globais de uma aplicação web estática tenham a menor latência possível ao acessar imagens hospedadas no S3. Qual serviço deve ser integrado?
- A) Amazon CloudFront.
- B) AWS Global Accelerator.
- C) Amazon Route 53 com Latency Routing.
- D) AWS Direct Connect.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: A**
> * **Por que está certa:** O CloudFront é a CDN da AWS que faz cache de conteúdo estático em Edge Locations perto dos usuários.
> * **Distratores:** B (acelera tráfego IP fixo/UDP, não foca em cache de objetos), C (Roteia DNS, mas não entrega o conteúdo), D (Link privado para o data center).

</details>

---

### 4. Qual recurso do AWS Organizations permite que um administrador central defina o teto máximo de permissões que as contas membro podem ter, independentemente das políticas do IAM locais?
- A) Service Control Policies (SCPs).
- B) Resource-based Policies.
- C) IAM Groups.
- D) AWS Trusted Advisor.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: A**
> * **Por que está certa:** SCPs são a ferramenta de governança do AWS Organizations para limitar o que as contas membro podem fazer (Guardrails).
> * **Distratores:** B (nasce no recurso), C (agrupa usuários, não restringe contas), D (dá dicas, não impõe bloqueios).

</details>

---

### 5. Uma aplicação financeira precisa processar mensagens em uma ordem estrita (First-In, First-Out) e garantir que nenhuma mensagem seja processada em duplicidade. Qual serviço de mensageria deve ser utilizado?
- A) Amazon SNS.
- B) Amazon SQS Standard Queue.
- C) Amazon SQS FIFO Queue.
- D) Amazon EventBridge.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C**
> * **Por que está certa:** SQS FIFO garante a ordem exata de processamento e possui deduplicação nativa.
> * **Distratores:** A (notificação, não fila durável), B (SQS Standard não garante ordem estrita), D (barramento de eventos).

</details>

---

### 6. Um desenvolvedor precisa de um ambiente de desenvolvimento rápido na nuvem, acessível via navegador, para codar e depurar aplicações de forma colaborativa. Qual serviço atende a esse requisito?
- A) AWS Cloud9.
- B) Amazon CodeCommit.
- C) AWS CodePipeline.
- D) Amazon WorkSpaces.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: A**
> * **Por que está certa:** Cloud9 é um IDE baseado em nuvem que roda no navegador e permite colaboração em tempo real.
> * **Distratores:** B (repositório Git), C (orquestrador CI/CD), D (desktop virtual completo).

</details>

---

### 7. Uma empresa quer monitorar continuamente a conformidade de suas instâncias EC2 contra uma regra que proíbe o uso de portas SSH abertas para o mundo (0.0.0.0/0). Qual serviço automatiza essa auditoria de configuração?
- A) AWS CloudTrail.
- B) Amazon CloudWatch.
- C) AWS Config.
- D) Amazon Inspector.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C**
> * **Por que está certa:** AWS Config registra o histórico de configurações e avalia se elas estão em conformidade com regras definidas (como "sem porta 22 aberta").
> * **Distratores:** A (registra QUEM fez a ação), B (métricas operacionais), D (escaneia vulnerabilidades de software).

</details>

---

### 8. Qual ferramenta da AWS fornece recomendações para realizar o "Right Sizing" de instâncias EC2, sugerindo tipos de instância que melhor se adaptam à carga de trabalho real para otimizar custos?
- A) AWS Compute Optimizer.
- B) AWS Budgets.
- C) AWS Pricing Calculator.
- D) AWS Cost Explorer.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: A**
> * **Por que está certa:** Compute Optimizer usa Machine Learning para analisar o uso histórico e sugerir a instância ideal (nem maior, nem menor que o necessário).
> * **Distratores:** B (alertas de custo), C (estima antes de gastar), D (analisa gastos passados).

</details>

---

### 9. Uma aplicação de e-commerce armazena milhões de fotos de produtos no S3. O padrão de acesso a essas fotos é desconhecido e muda constantemente. Qual classe de armazenamento oferece a melhor relação custo-benefício automatizada?
- A) S3 Standard.
- B) S3 Intelligent-Tiering.
- C) S3 Standard-Infrequent Access (IA).
- D) S3 Glacier Instant Retrieval.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B**
> * **Por que está certa:** Intelligent-Tiering é a única classe que move arquivos automaticamente entre camadas frequentes e infrequentes sem taxas de recuperação, ideal para padrões desconhecidos.
> * **Distratores:** A (acesso frequente caro), C (exige padrão conhecido e cobra recuperação), D (arquivamento).

</details>

---

### 10. Qual serviço inteligente detecta automaticamente tentativas de mineração de criptomoedas e comportamentos anômalos de rede em sua conta AWS sem a necessidade de agentes?
- A) AWS WAF.
- B) Amazon GuardDuty.
- C) AWS Shield Advanced.
- D) Amazon Macie.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B**
> * **Por que está certa:** GuardDuty analisa logs de rede (VPC Flow Logs, DNS logs) e CloudTrail para detectar ameaças como Crypto Mining.
> * **Distratores:** A (firewall de camada 7), C (protege contra DDoS), D (caça dados sensíveis PII).

</details>

---

### 11. Uma empresa precisa estabelecer uma conexão de rede física, dedicada e privada entre seu data center local e a AWS para garantir latência consistente. Qual serviço deve ser contratado?
- A) AWS Site-to-Site VPN.
- B) AWS Client VPN.
- C) AWS Direct Connect.
- D) Amazon VPC Peering.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C**
> * **Por que está certa:** Direct Connect é um link físico dedicado.
> * **Distratores:** A (VPN via internet), B (acesso remoto de usuários), D (conecta duas VPCs).

</details>

---

### 12. Um cliente do plano de suporte Business deseja assistência para preparar sua infraestrutura para um evento de lançamento de produto que gerará um pico massivo de tráfego. Qual recurso he deve solicitar (sujeito a taxas extras)?
- A) Technical Account Manager (TAM).
- B) Infrastructure Event Management (IEM).
- C) AWS Support Concierge.
- D) AWS Trusted Advisor.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B**
> * **Por que está certa:** IEM é um engajamento de suporte para lançamentos críticos (como Black Friday), ajudando a evitar quedas.
> * **Distratores:** A (TAM é para plano Enterprise fixo), C (ajuda com faturamento), D (automatizado).

</details>

---

### 13. Qual serviço da AWS permite consultar dados armazenados no Amazon S3 diretamente usando comandos SQL padrão, sem a necessidade de carregar os dados em um banco de dados relacional?
- A) Amazon Redshift Spectrum.
- B) Amazon Athena.
- C) Amazon RDS for PostgreSQL.
- D) AWS Glue DataBrew.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B**
> * **Por que está certa:** Athena é serverless e permite rodar SQL direto em arquivos CSV/JSON/Parquet no S3.
> * **Distratores:** A (extensão do Redshift para S3, exige cluster), C (banco relacional tradicional), D (preparação visual de dados).

</details>

---

### 14. Qual pilar do AWS Well-Architected Framework foca no uso de serviços gerenciados para reduzir a carga de manutenção de infraestrutura e na automação de processos de mudança?
- A) Operational Excellence.
- B) Security.
- C) Performance Efficiency.
- D) Reliability.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: A**
> * **Por que está certa:** Excelência Operacional foca em automação, melhoria contínua e uso de código para gerenciar infraestrutura.
> * **Distratores:** B (proteção), C (uso eficiente de recursos), D (resiliência/DR).

</details>

---

### 15. Uma empresa deseja migrar um banco de dados Oracle on-premises para o Amazon Aurora. Qual ferramenta deve ser usada para converter o esquema (schema) do banco de dados para que ele seja compatível com a nova engine?
- A) AWS Database Migration Service (DMS).
- B) AWS Schema Conversion Tool (SCT).
- C) AWS Migration Hub.
- D) AWS Application Discovery Service.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B**
> * **Por que está certa:** SCT converte o código do banco (stored procedures, views) entre engines diferentes (ex: Oracle para Aurora). O DMS move os DADOS.
> * **Distratores:** A (move dados, não converte o código complexo do esquema), C (portal de migração), D (inventário).

</details>

---

## 🎯 Gatilho de Exame

Para não travar nas difíceis, use o **Método da Exclusão Cirúrgica**:

1.  **Identifique o Verbo:** Se a questão pede "Detectar", pense em GuardDuty ou Inspector. Se pede "Proteger", pense em WAF ou Shield. Se pede "Registrar/Auditar", pense em CloudTrail ou Config.
2.  **Custo vs. Performance:** Se a alternativa oferece uma performance absurda mas o enunciado pede "Custo Mínimo", descarte-a. A AWS raramente coloca a opção mais cara como gabarito, a menos que o termo seja "Mission Critical".
3.  **Gerenciado vs. Manual:** Sempre prefira a resposta que tira o trabalho manual de você. Entre "Criar um script no Linux" e "Usar AWS Systems Manager", a AWS sempre quer que você use a ferramenta dela.
4.  **Atenção aos Detalhes:** Se o banco de dados pode parar à noite, é **On-Demand**. Se ele tem que ficar ligado 24/7 por 3 anos, é **Reserved**. Se a interrupção não dói, é **Spot**.

---

> **Sinal de Alerta:**
> 
> - **CapEx vs OpEx** ➔ Nuvem é OpEx (pague pelo que usa), Data Center tradicional é CapEx (investimento físico alto).
> - **Stateful vs Stateless** ➔ Security Groups são stateful (lembram do tráfego de ida), NACLs são stateless (precisam de regras explícitas para ida e volta).
> - **Trusted Advisor vs Inspector** ➔ Trusted Advisor olha a conta como um todo (custo, segurança geral, performance), enquanto o Inspector foca em vulnerabilidades de instâncias e imagens de container.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 10: Simulado Completo CLF-C02 - Versão 1 - Reta Final](02-simulado-completo-v1-blueprint-real.md)
* [➡️ Módulo 10: Checklist Final: Prontidão e Aprovação (DoD)](04-checklist-final-de-done-aprovacao.md)

---