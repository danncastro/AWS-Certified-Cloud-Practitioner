# 📝 Micro-Simulado: Fundamentos e Infraestrutura Global

Mano, papo reto: chegou a hora de validar se você realmente entendeu os fundamentos da AWS ou apenas decorou alguns nomes.

A prova da **AWS Certified Cloud Practitioner (CLF-C02)** testa sua capacidade de escolher a melhor solução para um cenário real.

Resolva as 20 questões abaixo simulando o ambiente de prova: sem consulta e foco total nas palavras de comando.

- ❌ Sem consulta.
- ⏱️ Controle o tempo.
- 🎯 Preste atenção às palavras-chave do enunciado.

---

## Questões

**1. Uma startup quer lançar um novo recurso e precisa de servidores imediatamente, sem passar por processos de aquisição de hardware que levam semanas. Qual característica da computação em nuvem permite essa agilidade?**

- A) Massive economies of scale.
- B) On-demand self-service.
- C) High availability.
- D) Resource pooling.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B (On-demand self-service)**
> 
> * **Por que é a certa:** O "On-demand self-service" permite que você obtenha recursos de TI de forma automática através de uma API ou console, sem intervenção humana da AWS.
> * **A pegadinha:** "Agility" é o benefício final, mas a característica técnica que entrega isso é o autoatendimento sob demanda.
</details>

---

**2. Ao migrar para a AWS, uma empresa percebe que o custo unitário dos serviços diminui conforme o volume total de uso de todos os clientes da AWS aumenta. A qual conceito isso se refere?**

- A) Pay-as-you-go pricing.
- B) Scalability.
- C) Massive economies of scale.
- D) Agility.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C (Massive economies of scale)**
> 
> * **Por que é a certa:** Economia de escala massiva é o princípio onde o volume total de clientes permite à AWS baixar seus custos operacionais e repassar isso como preços menores.
> * **A pegadinha:** "Pay-as-you-go" é como você paga, mas o motivo do preço cair pelo volume é a economia de escala.
</details>

---

**3. Um arquiteto de soluções está desenhando uma aplicação que deve permanecer online mesmo se um data center inteiro sofrer uma inundação catastrófica. Qual estratégia de infraestrutura global ele deve adotar?**

- A) Deploy em uma única Edge Location.
- B) Deploy em múltiplas Availability Zones (AZs).
- C) Uso de instâncias EC2 maiores (Vertical Scaling).
- D) Uso de um único bucket S3 na região us-east-1.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B (Deploy em múltiplas Availability Zones (AZs))**
> 
> * **Por que é a certa:** Múltiplas AZs garantem alta disponibilidade. Como elas são fisicamente separadas, um desastre em uma zona não afeta a outra.
> * **A pegadinha:** "Vertical Scaling" (instância maior) não ajuda se o data center onde ela está inundar.
</details>

---

**4. No modelo financeiro da AWS, qual é a principal vantagem de trocar Capital Expenditure (CapEx) por Operational Expenditure (OpEx)?**

- A) Ter controle total sobre a manutenção física dos racks.
- B) Trocar custos variáveis por investimentos iniciais pesados.
- C) Eliminar a necessidade de monitorar custos.
- D) Substituir investimentos pesados antecipados por custos variáveis baseados no uso.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: D (Substituir investimentos pesados antecipados por custos variáveis baseados no uso)**
> 
> * **Por que é a certa:** A nuvem transforma o custo fixo (CapEx) em custo variável operacional (OpEx), pagando apenas pelo que consome.
> * **A pegadinha:** A alternativa B inverte os conceitos (dizendo para trocar variável por fixo), cuidado na leitura!
</details>

---

**5. Uma empresa precisa garantir que seus dados de clientes não saiam do território nacional por motivos de leis de soberania de dados. Qual componente da infraestrutura global deve ser o critério principal para essa escolha?**

- A) Edge Locations.
- B) Availability Zones.
- C) AWS Regions.
- D) VPC Endpoints.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C (AWS Regions)**
> 
> * **Por que é a certa:** AWS Regions são localizações geográficas isoladas. Para manter dados em um país, você deve escolher a região desse país.
> * **A pegadinha:** Edge Locations são apenas para cache de conteúdo e existem em centenas de lugares, não servem para controle de residência de dados principal.
</details>

---

**6. Qual é a função principal das AWS Edge Locations dentro da rede global da AWS?**

- A) Rodar instâncias EC2 pesadas perto do desenvolvedor.
- B) Hospedar bancos de dados relacionais Multi-AZ.
- C) Fazer cache de conteúdo para reduzir a latência para os usuários finais.
- D) Prover isolamento de falhas para o plano de controle do IAM.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C (Fazer cache de conteúdo para reduzir a latência para os usuários finais)**
> 
> * **Por que é a certa:** Edge Locations são pontos de presença para o Amazon CloudFront fazer cache de conteúdo perto do usuário, reduzindo a latência.
> * **A pegadinha:** Você não lança instâncias EC2 (computação pesada) ou RDS (banco) em Edge Locations.
</details>

---

**7. Segundo o Modelo de Responsabilidade Compartilhada, quem é o responsável pelo descarte físico de discos rígidos obsoletos nos data centers?**

- A) O cliente.
- B) A AWS.
- C) O Technical Account Manager (TAM).
- D) O provedor de internet (ISP).

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B (A AWS)**
> 
> * **Por que é a certa:** A AWS cuida da segurança "DA" nuvem, o que inclui a infraestrutura física e o hardware dos data centers.
> * **A pegadinha:** O cliente nunca toca no hardware físico da AWS.
</details>

---

**8. Um desenvolvedor precisa de uma solução onde ele apenas faça o deploy do código da aplicação e a AWS gerencie automaticamente o provisionamento, escalonamento e patches do sistema operacional. Qual modelo de serviço é esse?**

- A) Infrastructure as a Service (IaaS).
- B) Software as a Service (SaaS).
- C) Platform as a Service (PaaS).
- D) Desktop as a Service (DaaS).

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C (Platform as a Service (PaaS))**
> 
> * **Por que é a certa:** PaaS (como o Elastic Beanstalk) remove a gestão do SO e da infra subjacente, deixando o dev focado apenas no código.
> * **A pegadinha:** No IaaS (EC2), você ainda teria que gerenciar o SO e os patches.
</details>

---

**9. No contexto de Controles Compartilhados (Shared Controls), como funciona a responsabilidade pelo Patch Management?**

- A) É responsabilidade exclusiva da AWS aplicar patches em tudo, incluindo instâncias EC2.
- B) É responsabilidade exclusiva do cliente aplicar patches em toda a infraestrutura global.
- C) A AWS aplica patches na infraestrutura física e serviços gerenciados; o cliente aplica no Guest OS das instâncias EC2.
- D) O Patch Management não é um controle compartilhado, mas sim um serviço de SaaS.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C (A AWS aplica patches na infraestrutura física e serviços gerenciados; o cliente aplica no Guest OS das instâncias EC2)**
> 
> * **Por que é a certa:** O gerenciamento de patches é um controle compartilhado clássico. A AWS cuida da infra base e o cliente cuida das suas instâncias.
> * **A pegadinha:** Dizer que a AWS cuida de tudo ou que o cliente cuida de tudo é ignorar a divisão do modelo de responsabilidade.
</details>

---

**10. Qual conceito descreve a capacidade de um sistema crescer para suportar um aumento contínuo de carga sem perder performance?**

- A) Elasticidade.
- B) Escalabilidade.
- C) Agilidade.
- D) Durabilidade.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B (Escalabilidade)**
> 
> * **Por que é a certa:** Escalabilidade é sobre aguentar o crescimento mantendo a performance.
> * **A pegadinha:** Elasticidade é o ato de "esticar e puxar" conforme a demanda oscila, mas a capacidade de crescer sustentadamente é escalabilidade.
</details>

---

**11. Uma empresa quer rodar um workload que pode ser interrompido a qualquer momento para obter o máximo de desconto (até 90%) no custo de computação. Qual opção de compra de instâncias EC2 deve ser usada?**

- A) On-Demand Instances.
- B) Reserved Instances.
- C) Dedicated Hosts.
- D) Spot Instances.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: D (Spot Instances)**
> 
> * **Por que é a certa:** Spot Instances oferecem os maiores descontos em troca de usar capacidade ociosa que pode ser recuperada pela AWS a qualquer momento.
> * **A pegadinha:** Reserved Instances dão desconto, mas exigem compromisso de tempo, não aceitam interrupção.
</details>

---

**12. Qual pilar do AWS Well-Architected Framework foca em evitar gastos desnecessários e entregar valor de negócio pelo menor preço possível?**

- A) Reliability.
- B) Security.
- C) Cost Optimization.
- D) Operational Excellence.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C (Cost Optimization)**
> 
> * **Por que é a certa:** O pilar de Otimização de Custos foca exatamente no equilíbrio entre performance e menor custo possível.
> * **A pegadinha:** Operational Excellence foca em processos e automação de rotina, não especificamente no custo.
</details>

---

**13. No Modelo de Responsabilidade Compartilhada, qual das seguintes ações é responsabilidade exclusiva do cliente?**

- A) Manutenção dos cabos de fibra óptica entre as Regiões.
- B) Configuração de Security Groups e Network ACLs.
- C) Treinamento dos funcionários que cuidam da segurança física dos data centers.
- D) Atualização do firmware dos roteadores de borda da AWS.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B (Configuração de Security Groups e Network ACLs)**
> 
> * **Por que é a certa:** Configurar quem entra e sai das instâncias (Security Groups) é segurança "NA" nuvem, responsabilidade do cliente.
> * **A pegadinha:** Tudo que envolve hardware, cabos ou funcionários físicos dos data centers é responsabilidade da AWS.
</details>

---

**14. Qual ferramenta da AWS permite que um cliente revise sua arquitetura contra as melhores práticas dos 6 pilares e receba recomendações de melhoria?**

- A) AWS Trusted Advisor.
- B) AWS Well-Architected Tool.
- C) AWS Pricing Calculator.
- D) AWS Budgets.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B (AWS Well-Architected Tool)**
> 
> * **Por que é a certa:** A Well-Architected Tool é a ferramenta de autoatendimento para aplicar o framework de 6 pilares.
> * **A pegadinha:** O Trusted Advisor dá recomendações automáticas, mas não é a ferramenta principal para revisar contra o Well-Architected Framework.
</details>

---

**15. Uma empresa quer conectar seu data center local à AWS de forma permanente, usando uma conexão física dedicada que não passe pela internet pública. Qual serviço deve ser usado?**

- A) AWS Site-to-Site VPN.
- B) AWS Outposts.
- C) AWS Direct Connect.
- D) Amazon CloudFront.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C (AWS Direct Connect)**
> 
> * **Por que é a certa:** O Direct Connect é um link físico dedicado e privado entre a empresa e a AWS.
> * **A pegadinha:** O Site-to-Site VPN é criptografado, mas passa pela internet pública.
</details>

---

**16. Qual das seguintes afirmações sobre Availability Zones (AZs) está correta?**

- A) Cada AZ consiste em um único servidor físico.
- B) AZs em uma região são conectadas por redes de ultra-baixa latência.
- C) Todas as AZs de uma região compartilham a mesma fonte de energia.
- D) Uma AZ pode abranger múltiplas regiões geográficas.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B (AZs em uma região são conectadas por redes de ultra-baixa latência)**
> 
> * **Por que é a certa:** AZs são conectadas por fibra óptica de alta velocidade e baixa latência para permitir replicação síncrona.
> * **A pegadinha:** AZs possuem fontes de energia e rede redundantes e independentes (elas NÃO compartilham os mesmos pontos de falha).
</details>

---

**17. Uma aplicação foi desenhada para "parar de adivinhar a capacidade" (Stop guessing capacity). Isso significa que ela utiliza qual recurso para ajustar os recursos automaticamente?**

- A) IAM Policies.
- B) Auto Scaling.
- C) CloudTrail logs.
- D) AWS Artifact reports.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B (Auto Scaling)**
> 
> * **Por que é a certa:** O Auto Scaling permite que os recursos subam ou desçam conforme a métrica, evitando que você precise prever (adivinhar) o pico.
> * **A pegadinha:** IAM Policies tratam de permissão, não de capacidade de infraestrutura.
</details>

---

**18. Qual modelo de implantação de nuvem envolve manter alguns servidores localmente e estender parte da capacidade para a nuvem AWS?**

- A) Public Cloud.
- B) Private Cloud.
- C) Hybrid Cloud.
- D) Multicloud.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C (Hybrid Cloud)**
> 
> * **Por que é a certa:** Nuvem Híbrida é a combinação de ambiente local (on-premises) com nuvem pública.
> * **A pegadinha:** Public Cloud é 100% na AWS; Private Cloud é 100% no local.
</details>

---

**19. No Modelo de Responsabilidade Compartilhada para o Amazon RDS (PaaS), pelo que a AWS é responsável?**

- A) Gerenciar as contas de usuário dentro do banco de dados MySQL.
- B) Criptografar os dados em trânsito usando SSL/TLS.
- C) Aplicar patches de segurança no motor (engine) do banco de dados.
- D) Criar as tabelas e o esquema (schema) do banco de dados.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C (Aplicar patches de segurança no motor (engine) do banco de dados)**
> 
> * **Por que é a certa:** No RDS (serviço gerenciado/PaaS), a AWS cuida do SO e dos patches do motor do banco.
> * **A pegadinha:** O cliente ainda é o dono dos dados, das tabelas e de quem acessa o banco via IAM.
</details>

---

**20. O que significa o conceito de "Undifferentiated heavy lifting" que a AWS se propõe a resolver?**

- A) Tarefas de negócio exclusivas que geram lucro direto.
- B) Tarefas de infraestrutura repetitivas (racks, energia, rede) que não agregam valor direto ao produto final.
- C) O esforço de codificar a lógica de negócio principal da aplicação.
- D) O processo de marketing de uma nova aplicação na nuvem.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B (Tarefas de infraestrutura repetitivas (racks, energia, rede) que não agregam valor direto ao produto final)**
> 
> * **Por que é a certa:** O "trabalho pesado indiferenciado" são as tarefas chatas de infra que toda empresa faz igual e que não as torna únicas. Deixar isso para a AWS libera seu time para inovar.
> * **A pegadinha:** Codificar a lógica de negócio é o "diferenciado", é o que traz dinheiro para a empresa.
</details>

---

## 🎯 Gatilho de Exame

Mano, para ler enunciados de simulados na velocidade da luz, procure por estes pares de "Problema ➔ Solução":

* **Pico de tráfego/Ajuste automático** ➔ Elasticidade / Auto Scaling.
* **Reduzir latência global** ➔ Edge Locations / CloudFront.
* **Soberania de dados / Leis locais** ➔ AWS Regions.
* **Menor esforço operacional** ➔ Serviços Gerenciados / Serverless (Lambda).
* **Workload interrompível / Barato** ➔ Spot Instances.
* **Audit API / Quem fez o quê** ➔ CloudTrail.
* **Performance metrics / Uso de CPU** ➔ CloudWatch.
* **Segurança física / Hardware** ➔ Responsabilidade da AWS.
* **Dados / Permissões / Patches de EC2** ➔ Responsabilidade do Cliente.
* **Relatórios de ISO/PCI/SOC** ➔ AWS Artifact.

---

## 💡 Dica de Ouro

Durante a prova, procure sempre pelas palavras-chave do enunciado.

Se aparecer:

- **Most cost-effective** → escolha a solução de menor custo.
- **Least operational overhead** → escolha a solução mais gerenciada.
- **Highly available** → pense em múltiplas Availability Zones.
- **Low latency** → pense em Edge Locations ou Amazon CloudFront.
- **Data residency** → pense em AWS Regions.

Muitas questões são resolvidas apenas identificando essas palavras-chave.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Lab: Explorando a Infraestrutura Global da AWS](09-lab-explorando-infraestrutura-global.md)
* [➡️ IAM: Usuários, Grupos e Policies](../02-seguranca-identidade-e-conformidade/00-iam-usuarios-grupos-e-policies.md)
---
---