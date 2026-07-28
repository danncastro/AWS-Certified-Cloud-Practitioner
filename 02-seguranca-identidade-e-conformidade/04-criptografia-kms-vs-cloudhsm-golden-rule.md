# Criptografia: KMS vs. CloudHSM e a Regra de Ouro

No mundo da segurança, criptografia não é frescura, é sobrevivência. Na prova **AWS Certified Cloud Practitioner (CLF-C02)**, a AWS quer saber se você entende a diferença entre proteger um dado **armazenado** e um dado **em trânsito**, além de identificar qual serviço utilizar para gerenciar as chaves criptográficas.

---

## 1. Conceitos Fundamentais: Onde o dado mora?

Existem dois estados básicos da informação que você precisa proteger:

### Criptografia em Repouso (Encryption at Rest)

Protege os dados armazenados fisicamente em disco. Caso alguém obtenha acesso ao dispositivo de armazenamento, os dados continuam ilegíveis sem a chave de criptografia.

Exemplos de serviços que suportam criptografia em repouso:

- Amazon S3
- Amazon EBS
- Amazon EFS
- Amazon RDS
- Amazon DynamoDB

---

### Criptografia em Trânsito (Encryption in Transit)

Protege os dados durante a comunicação entre cliente e servidor, evitando ataques como **Man-in-the-Middle (MITM)**.

Tecnologias utilizadas:

- HTTPS (TLS/SSL)
- **AWS Certificate Manager (ACM)** para emissão e gerenciamento de certificados TLS.

> **Importante:** O ACM não realiza a criptografia. Ele apenas gerencia os certificados digitais utilizados pelos protocolos TLS/HTTPS.

---

## 2. AWS KMS: Simplicidade e Integração Nativa

O **AWS Key Management Service (KMS)** é o serviço padrão da AWS para criação e gerenciamento de chaves criptográficas.

*   **Totalmente Gerenciado:** A AWS cuida da alta disponibilidade e da segurança física do hardware que guarda as chaves.
*   **Multi-tenant:** O hardware é compartilhado com outros clientes, mas as chaves são isoladas logicamente para você.
*   **Integração Nativa:** Com um clique, você criptografa um Bucket S3 ou um volume EBS.
*   **Compliance:** Atende ao padrão **FIPS 140-2 Level 2** (com algumas funções em Level 3).

Outro detalhe importante:

- As chaves nunca deixam o KMS em texto puro.

~~~mermaid
graph LR
    A[Usuário/App] --> B{AWS KMS}
    B --> C[S3]
    B --> D[EBS]
    B --> E[RDS]
    subgraph "Gerenciamento AWS"
    B
    end
~~~

~~~mermaid
flowchart LR

App["Aplicação"]

KMS["AWS KMS"]

App --> KMS

KMS --> S3["Amazon S3"]
KMS --> EBS["Amazon EBS"]
KMS --> RDS["Amazon RDS"]
KMS --> EFS["Amazon EFS"]
~~~

### Quando usar?

Sempre que o objetivo for:

- simplicidade;
- integração automática com serviços AWS;
- menor esforço operacional;
- gerenciamento totalmente administrado pela AWS.


---

## 3. AWS CloudHSM: Hardware Dedicado e Controle Total

O **AWS CloudHSM** é para quem joga no modo "Hardcore" de conformidade. Ele entrega um módulo de segurança de **Hardware Security Module (HSM)**  físico e dedicado dentro da sua própria VPC.

Diferente do KMS, o hardware é exclusivo para sua organização.


**Single-tenant:** O hardware é exclusivo seu. Ninguém mais encosta ali.
**Controle Exclusivo:** A AWS não tem acesso às suas chaves. Se você perder as credenciais do HSM, já era, nem o suporte da AWS recupera.
**Conformidade Rígida:** Focado em atender o padrão FIPS 140-2 Level 3.
**Protocolos de Indústria:** Usa APIs padrão de mercado como PKCS#11, JCE (Java) e Microsoft CNG.

> A AWS não possui acesso às suas chaves.

Como utiliza APIs padrão da indústria, aplicações legadas conseguem utilizar o ***CloudHSM*** com poucas adaptações.

---

## 4. A Regra de Ouro (Golden Rule) de Decisão

Não perca tempo na prova. Se ler o enunciado e vir esses gatilhos, marque sem medo:
Se o requisito for... A resposta é...
	
| Requisito | Serviço | Motivo |
|-----------|----------|--------|
| Simplicidade e integração com serviços AWS | **AWS KMS** | Serviço totalmente gerenciado |
| Criptografia do Amazon S3, EBS ou RDS | **AWS KMS** | Integração nativa |
| Menor esforço operacional | **AWS KMS** | A AWS administra toda a infraestrutura |
| Hardware dedicado | **AWS CloudHSM** | HSM exclusivo |
| Controle exclusivo das chaves | **AWS CloudHSM** | Apenas o cliente possui acesso |
| Requisitos rígidos de conformidade (FIPS 140-2 Level 3) | **AWS CloudHSM** | Hardware dedicado certificado |

---                                                                                                                                                                               

## 5. AWS KMS vs AWS CloudHSM

| Característica | AWS KMS | AWS CloudHSM |
|---------------|---------|--------------|
| Totalmente gerenciado | ✅ | ❌ |
| Hardware dedicado | ❌ | ✅ |
| Multi-tenant | ✅ | ❌ |
| Single-tenant | ❌ | ✅ |
| Integração automática com serviços AWS | ✅ | Limitada |
| Menor esforço operacional | ✅ | ❌ |
| Controle exclusivo das chaves | ❌ | ✅ |
| Melhor escolha para a maioria dos workloads | ✅ | ❌ |

---

## 6. Conceitos Importantes

Alguns termos aparecem frequentemente na documentação da AWS.

### Customer Managed Keys (CMK)

Chaves criadas e administradas pelo cliente dentro do KMS.

### AWS Managed Keys

Chaves criadas automaticamente pela AWS para determinados serviços.

### AWS Owned Keys

Chaves totalmente administradas pela AWS e invisíveis para o cliente.

### Envelope Encryption

Técnica utilizada pelo KMS na qual os dados são criptografados utilizando uma **Data Key**, enquanto essa chave é protegida por uma chave mestra armazenada no KMS.

---

## 🎯 Gatilho de Exame

Associe estes termos às soluções corretas.

- **Encryption at Rest** → Dados armazenados em disco (S3, EBS, EFS, RDS, DynamoDB).
- **Encryption in Transit** → Dados se movendo (HTTPS / TLS).
- **AWS KMS** → Serviço regional, gerenciado, integrado e multi-tenant.
- **AWS CloudHSM** → Hardware Security Module single-tenant, dedicado.
- **Hardware Security Module (HSM)** → CloudHSM.
- **Single-tenant** → CloudHSM.
- **Multi-tenant** → KMS.
- **Envelope Encryption** → Técnica utilizada pelo KMS.
- **Customer Managed Keys (CMK)** → Chaves criadas pelo cliente no KMS.
- **AWS Managed Keys** → Chaves gerenciadas automaticamente pela AWS.
- **FIPS 140-2 Level 3 compliance:** Gatilho definitivo para CloudHSM.

> **Observação:** A CLF-C02 normalmente **não aprofunda** em criptografia simétrica versus assimétrica. O importante é saber que o **KMS gerencia chaves criptográficas utilizadas pelos serviços da AWS**.

---

> ⚠️ **Pegadinha de Simulado**
>
> O **AWS KMS** gerencia chaves criptográficas, mas **não substitui protocolos como TLS/HTTPS**.
>
> - Para proteger **dados em trânsito**, utilize **TLS/HTTPS** (geralmente com certificados do ACM).
> - Para proteger **dados armazenados**, utilize **Encryption at Rest**, normalmente integrada ao **AWS KMS**.
>
> Outra pegadinha comum é afirmar que o KMS é a única forma de criptografar dados. Isso é falso. Também é possível utilizar **Client-Side Encryption**, onde os dados são criptografados antes mesmo de serem enviados para a AWS.

---

* [🏠 Menu Principal](../README.md)
* [⬅️ Proteção contra DDoS: AWS Shield e AWS WAF](03-protecao-contra-ddos-shield-e-waf.md)
* [➡️ Gestão de Segredos: Secrets Manager vs. Parameter Store](05-gestao-de-segredos-secrets-manager-vs-parameter-store.md)

---
---