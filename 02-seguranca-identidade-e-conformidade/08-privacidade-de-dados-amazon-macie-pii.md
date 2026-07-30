# Privacidade de Dados: Amazon Macie e Proteção de PII

No mundo atual, dado é o novo petróleo, mas se você vazar dados sensíveis dos seus clientes, esse petróleo vira um incêndio incontrolável. Quando falamos em segurança na AWS, proteger a infraestrutura é apenas parte do trabalho. Também é necessário proteger **os dados**.

É exatamente esse o papel do **Amazon Macie**.

O Macie é um serviço totalmente gerenciado que utiliza **Machine Learning (ML)** e análise de padrões para descobrir, classificar e proteger informações sensíveis armazenadas no **Amazon S3**.

Sua principal missão é responder perguntas como:

- Onde existem dados sensíveis?
- Existem buckets públicos contendo informações críticas?
- Há risco de violação da LGPD ou GDPR?

---

## 1. O que é o Amazon Macie?

O **Amazon Macie** é um serviço de segurança e privacidade de dados totalmente gerenciado **(Data Security)** . Ele usa **Machine Learning** e identificação de padrões (pattern matching) para descobrir, classificar e proteger dados sensíveis que estão "escondidos" dentro dos seus buckets no **Amazon S3**.

O Macie automatiza o trabalho que seria impossível fazer na mão: abrir arquivo por arquivo, imagem por imagem, e checar se ali tem algo que não deveria estar exposto.

Ele realiza análises automáticas dos objetos armazenados nos buckets para identificar informações confidenciais e problemas de segurança.

Entre suas funções estão:

- Descobrir dados sensíveis
- Classificar informações
- Detectar exposição indevida
- Gerar Findings automaticamente
- Auxiliar em auditorias de conformidade

Tudo isso ocorre sem que você precise abrir manualmente cada arquivo.

---

## 2. O Conceito de PII (Informações de Identificação Pessoal)

Para a prova e para o dia a dia, você precisa saber o que é **PII (Personally Identifiable Information)**. Basicamente, é qualquer dado que possa ser usado para identificar uma pessoa específica.

**Exemplos clássicos que o Macie caça:**
*   **Documentos de Identificação:** CPF, RG, SSN (Social Security Number), passaportes.
*   **Dados Financeiro:** Números de cartão de crédito, contas bancárias.
*   **Informações de Contato:** Nomes completos, e-mails, endereços físicos, números de telefone.
*   **Saúde (PHI):** Registros médicos e históricos de pacientes.

---

## 3. Como o Macie funciona?

O Macie realiza uma varredura automática dos objetos armazenados no Amazon S3.

Durante a análise ele utiliza:

- Machine Learning
- Pattern Matching
- Expressões regulares
- Inteligência para classificação de dados

Quando encontra informações sensíveis, gera um **Finding**.

---

### Exemplo

Imagine um bucket contendo um arquivo:

~~~text
clientes.csv
~~~

Conteúdo:

~~~text
Nome,CPF,Telefone
João,123.456.789-00,(11)99999-9999
Maria,987.654.321-00,(21)98888-8888
~~~

Durante a análise, o Macie identifica padrões compatíveis com CPF e telefone.

Resultado:

- Bucket classificado como contendo PII
- Finding gerado
- Risco elevado reportado


---

## 3. Os Dois Pilares do Amazon Macie

O Macie não faz apenas uma coisa; ele atua em duas frentes críticas para a sua postura de segurança no S3:

### A. Descoberta Automatizada de Dados Sensíveis
O Macie realiza varreduras (inventory/discovery jobs) nos seus buckets. Ele analisa o conteúdo dos objetos e gera alertas automáticos se encontrar PII. 
*   **Cenário:** Se você subir um arquivo `.csv` com 50.000 CPFs em um bucket, o Macie vai te avisar que aquele bucket contém dados altamente sensíveis.

### B. Avaliação de Postura de Segurança (Bucket Security)
Ele monitora continuamente a configuração dos seus buckets para identificar riscos de exposição. Ele te entrega um inventário mostrando:
*   Buckets que estão **públicos** (abertos para a internet).
*   Buckets que **não possuem criptografia** habilitada.
*   Buckets que são compartilhados com contas fora da sua organização.

---

### Exemplo de Cenário

Imagine uma empresa que possui centenas de buckets S3.

Um desenvolvedor publica acidentalmente um bucket contendo:

- 80 mil CPFs
- Cartões de crédito
- Endereços
- Dados financeiros

O Macie:

- identifica os dados sensíveis;
- informa o nível de criticidade;
- aponta o bucket afetado;
- gera Findings;
- auxilia na correção.

---

## 4. Conformidade: LGPD e GDPR

Se a sua empresa precisa seguir leis de privacidade como a **LGPD** (Brasil) ou a **GDPR** (Europa), o Amazon Macie é o seu melhor amigo. Ele fornece as evidências e a automação necessárias para provar que você sabe onde os dados sensíveis estão e que eles estão protegidos. Ele ajuda a responder auditorias e a mitigar o risco de multas pesadas por vazamento de informações pessoais.

---

### Compliance

O Macie é amplamente utilizado para atender normas de conformidade como:

- LGPD
- GDPR
- HIPAA
- PCI DSS

Ele ajuda empresas a:

- localizar dados pessoais;
- identificar riscos;
- produzir evidências para auditorias.

---

## 5. Amazon Macie vs Outros Serviços

Essa comparação cai bastante em prova.

| Serviço | Especialidade |
|----------|---------------|
| Macie | Descobrir dados sensíveis (PII) |
| GuardDuty | Detectar ameaças |
| Inspector | Encontrar vulnerabilidades |
| Security Hub | Centralizar Findings |
| CloudTrail | Auditoria de ações |

---

### Fluxo Simplificado

~~~mermaid
flowchart LR

    S3["🪣 Amazon S3 Bucket"]

    M["🔎 Amazon Macie"]

    F["📋 Findings"]

    A["👨‍💻 Administrador"]

    S3 --> M

    M -->|"📄 Analisa conteúdo"| F
    M -->|"🆔 Detecta PII"| F
    M -->|"⚙️ Avalia configurações"| F

    F -->|"🚨 Alertas e recomendações"| A

    classDef storage fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef macie fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef findings fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;
    classDef admin fill:#F3E5F5,stroke:#8E24AA,stroke-width:2px;

    class S3 storage;
    class M macie;
    class F findings;
    class A admin;
~~~

---

### Integração com AWS Security Hub

Em ambientes corporativos é comum integrar o Macie ao Security Hub.

~~~mermaid
flowchart TD

    S3["🪣 Amazon S3"]

    M["🔎 Amazon Macie"]

    F["📋 Findings<br/>PII detectada"]

    H["🛡️ AWS Security Hub"]

    D["📊 Dashboard Centralizado"]

    S3 --> M
    M --> F
    F --> H
    H --> D

    classDef storage fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef macie fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef findings fill:#FDECEA,stroke:#D32F2F,stroke-width:2px;
    classDef hub fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;

    class S3 storage;
    class M macie;
    class F findings;
    class H,D hub;
~~~

Assim toda a equipe de segurança visualiza os Findings em um único painel.

---

## 6. Casos clássicos de prova

### Cenário 1

> Quero descobrir se existem CPFs armazenados em buckets S3.

Resposta:

**Amazon Macie**

---

### Cenário 2

> Preciso localizar cartões de crédito armazenados no S3.

Resposta:

**Amazon Macie**

---

### Cenário 3

> Quero identificar buckets públicos contendo dados sensíveis.

Resposta:

**Amazon Macie**

---

### Cenário 4

> Preciso atender requisitos da LGPD relacionados ao S3.

Resposta:

**Amazon Macie**

---

### Cenário 5

> Quero encontrar vulnerabilidades em uma instância EC2.

Resposta:

**Amazon Inspector**

---

### Cenário 6

> Quero detectar uma instância comprometida realizando mineração de criptomoedas.

Resposta:

**Amazon GuardDuty**

---

### O que o Macie NÃO faz?

O Macie não:

- monitora CPU;
- detecta ataques em tempo real;
- realiza scans de vulnerabilidades;
- protege aplicações web;
- escaneia bancos RDS diretamente.

Seu foco é praticamente um só:

> **Descobrir e proteger dados sensíveis armazenados no Amazon S3.**

---

### Resumo Rápido

| Recurso | Amazon Macie |
|----------|--------------|
| Machine Learning | ✅ |
| Descoberta de PII | ✅ |
| Classificação automática | ✅ |
| Amazon S3 | ✅ |
| Buckets públicos | ✅ |
| Buckets sem criptografia | ✅ |
| LGPD/GDPR | ✅ |
| Vulnerabilidades | ❌ |
| Ataques em tempo real | ❌ |

---

## Mnemônico

### Macie → "Meu Arquivo Contém Informações Escondidas"

Sempre que pensar em Macie, associe a:

- Dados
- Documentos
- Arquivos
- Privacidade
- Amazon S3

Macie "vasculha" seus buckets procurando informações que não deveriam estar expostas.

> **Guarde isso:**  o Amazon Macie é focado **exclusivamente no Amazon S3**. Ele não escaneia bancos de dados RDS ou instâncias EC2 diretamente. Se a questão falar de "PII no S3", o gabarito é Macie.

---

## 🎯 Gatilho de Exame

Se você ler estes termos em inglês, a resposta certa quase sempre envolverá o Macie:

| Termo em Inglês (Original) | O que o enunciado quer dizer na real |
| :--- | :--- |
| **Amazon Macie** | Serviço de privacidade para S3 usando ML. |
| **Personally Identifiable Information (PII)** | Dados sensíveis de pessoas (CPF, Cartão, etc). |
| **Data discovery and classification** | Descobrir e organizar o que é dado sensível no S3. |
| **Amazon S3 bucket security** | Avaliar se o bucket está público ou sem criptografia. |
| **Machine Learning data security** | O "motor" inteligente que o Macie usa para achar PII. |
| **GDPR / LGPD compliance** | Leis de privacidade que exigem proteção de PII. |

Se aparecer...

| Enunciado | Resposta |
|------------|----------|
| Personally Identifiable Information (PII) | Amazon Macie |
| Sensitive Data Discovery | Amazon Macie |
| Data Classification | Amazon Macie |
| Amazon S3 Data Security | Amazon Macie |
| Bucket Security Assessment | Amazon Macie |
| GDPR Compliance | Amazon Macie |
| LGPD Compliance | Amazon Macie |
| Credit Card Detection | Amazon Macie |
| CPF Detection | Amazon Macie |
| Machine Learning + S3 | Amazon Macie |

---

> **💡 Dica de Ouro:** Pense assim: **"Quero descobrir dados sensíveis?" → *Amazon Macie.* "Quero detectar ataques?" → *GuardDuty*. "Quero encontrar vulnerabilidades?" → *Inspector*. "Quero centralizar todos os Findings?" → *AWS Security Hub.***

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Detecção de Ameaças: GuardDuty (ML) vs. Inspector (Vulnerabilidades)](07-deteccao-de-ameacas-guardduty-ml-vs-inspector-vuln.md)
* [➡️ Conformidade e Relatórios: AWS Artifact](09-conformidade-e-relatorios-aws-artifact.md)

---
---