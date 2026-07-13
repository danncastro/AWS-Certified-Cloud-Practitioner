# 🔐 Modelo de Responsabilidade Compartilhada da Nuvem

Se existe um assunto que você **precisa dominar** para passar na **AWS Certified Cloud Practitioner (CLF-C02)**, é o **Shared Responsibility Model**.

A AWS **não** é uma "caixa preta" onde você envia sua aplicação e ela resolve tudo.

Existe uma divisão muito clara entre:

- o que é responsabilidade da AWS;
- o que é responsabilidade do cliente.

Essa separação aparece constantemente nas provas.

---

## 1. O Conceito e o Mantra Definitivo

A segurança na AWS funciona como um condomínio de luxo. O condomínio (AWS) cuida das cercas elétricas, das câmeras de vigilância, da guarita e da estrutura dos prédios. Você (o morador) é o único responsável por trancar a porta do seu apartamento, colocar senha no seu cofre e decidir quem você deixa entrar.

O mantra que você deve tatuar no cérebro para a prova é:
*   **AWS:** Segurança **DA** Nuvem (Security **OF** the Cloud).
*   **Cliente:** Segurança **NA** Nuvem (Security **IN** the Cloud).

A diferença entre **OF** e **IN** costuma ser o detalhe que decide a resposta correta.

---

## 2. Responsabilidade da AWS: Segurança DA Nuvem

A AWS cuida de toda a infraestrutura global que sustenta os serviços. Basicamente, tudo o que é **físico** ou camada de **virtualização base** é conta deles.

*   **Infraestrutura Física:** Proteção dos data centers, controle de acesso físico, câmeras, energia, refrigeração e segurança patrimonial.
*   **Rede Global:** Também é responsabilidade da AWS a segurança dos cabos de fibra óptica, roteadores, switches e backbone global que conectam as **Regions**, **Availability Zones (AZs)** e **Edge Locations**.
*   **Hardware e Software Base:** Manutenção física dos servidores (troca de discos, substituição de servidores, manutenção de memória, troca de processadores) e do **hipervisor** (o software que fatia o servidor físico em várias instâncias EC2).
*   **Serviços Gerenciados:** Em serviços totalmente gerenciados, como S3 ou DynamoDB, a AWS também cuida do sistema operacional da infraestrutura, da atualização do serviço e banco e a manutenção da plataforma, mas você continua responsável pelos seus dados e permissões de acesso..

---

## 3. Responsabilidade do Cliente: Segurança NA Nuvem

Aqui é onde o seu time trabalha. Tudo o que você "aperta o botão" ou configura no console é responsabilidade sua.

*   **Sistema Operacional (Guest OS):** Se você subiu uma instância EC2, a AWS te deu o hardware virtual, mas você é quem deve aplicar os **patches** de segurança e atualizações, antivírus, hardening e usuários locais.
*   **Configuração de Rede:** Você define quem entra e sai através dos **Security Groups** (firewalls de instância) e **NACLs** (firewalls de subnet) faz configuraçoes de VPC, Subnet e tabelas de rotas, a AWS fornece os recursos. ***Você define como eles serão utilizados.***.
*   **Criptografia:** A AWS fornece ferramentas (como o KMS e certificados), mas **você** tem que habilitar a criptografia de dados em repouso (**at rest**) e em trânsito (**in transit**).
*   **IAM (Identity and Access Management):** Todo gerenciamento de identidade pertence ao cliente, gerenciar usuários, criar senhas fortes, ativar **MFA** e definir políticas de acesso baseados no menor privilégio é 100% conta do cliente.
*   **Dados:** Você é o dono dos seus dados. Se você deixar um bucket S3 público por erro de configuração... A responsabilidade é sua não da AWS..

---

## 4. Controles Compartilhados (*Shared Controls*)

Existem áreas cinzentas onde ambos possuem responsabilidades, mas em perspectivas diferentes. A prova adora cobrar esses três exemplos:

*   **Patch Management (*Gerenciamento de Patches*):**
    *   **AWS:** Responsável por corrigir falhas na infraestrutura física, hiperviso e nos serviços gerenciados (como o motor do RDS).
    *   **Cliente:** Responsável por aplicar patches no sistema operacional das suas instâncias EC2(Linux e Windows) e nas suas aplicações, alem do software instalado.
*   **Configuration Management (*Gerenciamento de Configuração*):**
    *   **AWS:** Mantém a configuração dos dispositivos de infraestrutura física, rede global e software base.
    *   **Cliente:** Configura seus próprios recursos, como redes virtuais (VPC), security groups, políticas IAM, bancos de dados e instâncias EC2 alem de suas aplicaçoes instaladas.
*   **Awareness & Training (*Treinamento e Conscientização*):**
    *   **AWS:** Treina os próprios funcionários para manterem os data centers seguros.
    *   **Cliente:** Deve treinar seus funcionários e desenvolvedores sobre boas práticas de segurança na nuvem.

---

## Comparação Rápida

| AWS (Security **OF** the Cloud) | Cliente (Security **IN** the Cloud) |
|---------------------------------|--------------------------------------|
| Data Centers | Dados |
| Energia | IAM |
| Refrigeração | Usuários |
| Rede Global | Senhas |
| Servidores Físicos | MFA |
| Hardware | Sistema Operacional da EC2 |
| Hipervisor | Aplicações |
| Infraestrutura Base | Security Groups |
| Serviços Gerenciados | Configurações da Conta |

---

## 🎯 Gatilho de Exame

Se ler esses termos em inglês, associe imediatamente ao modelo de responsabilidade:

| Termo | O que significa |
|--------|-----------------|
| **Shared Responsibility Model** | Modelo que divide responsabilidades entre AWS e cliente. |
| **Security OF the Cloud** | Segurança da infraestrutura física mantida pela AWS. |
| **Security IN the Cloud** | Segurança dos recursos configurados pelo cliente. |
| **Shared Controls** | Responsabilidades compartilhadas entre AWS e cliente. |
| **Patch Management** | AWS atualiza a infraestrutura; cliente atualiza EC2 e aplicações. |
| **Configuration Management** | Cliente configura seus próprios recursos na nuvem. |
| **Awareness & Training** | Cada parte treina seus próprios colaboradores em segurança. |

---

## 🚨 Pegadinha de Prova

A AWS é responsável por:

- substituir discos defeituosos;
- destruir discos físicos no fim da vida útil;
- proteger os data centers.

Isso faz parte da:

> **Security OF the Cloud**

Já o cliente é responsável por:

- proteger os próprios dados;
- apagar informações quando necessário;
- configurar corretamente permissões de acesso.

Isso faz parte da:

> **Security IN the Cloud**

Sempre que a questão mencionar **dados, usuários, permissões ou configurações**, pense imediatamente:

> **Responsabilidade do Cliente.**

Se mencionar **hardware, data centers, rede global ou infraestrutura física**, a resposta normalmente será:

> **Responsabilidade da AWS.**

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Edge Locations e Amazon CloudFront](03-edge-locations-e-cloudfront-cache.md)
* [➡️ Detalhamento IaaS, PaaS e SaaS na Prática](05-detalhamento-iaas-paas-saas-na-pratica.md)

---
---