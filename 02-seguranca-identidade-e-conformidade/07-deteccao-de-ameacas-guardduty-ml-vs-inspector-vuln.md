# Detecção de Ameaças: GuardDuty (ML) vs. Inspector (Vulnerabilidades)

Na AWS existem diversos serviços de segurança, mas dois deles costumam aparecer juntos na prova da **AWS Certified Cloud Practitioner (CLF-C02)**: **Amazon GuardDuty** e **Amazon Inspector**.

A diferença é simples:

- **GuardDuty** procura **ameaças e comportamentos maliciosos em tempo real**.
- **Inspector** procura **vulnerabilidades** antes que elas sejam exploradas.

Essa distinção é uma das pegadinhas mais comuns do exame.

---

## 1. Amazon GuardDuty: O Guarda Inteligente

O **Amazon GuardDuty** é um serviço de **detecção inteligente de ameaças (Threat Detection)** e contínuo. Imagine ele como uma inteligência artificial que nunca dorme, monitorando tudo o que acontece na sua conta para achar comportamentos "esquisitos".

**Machine Learning (ML):** Ele usa ML para aprender o que é o comportamento normal da sua conta. Se, do nada, uma instância EC2 sua começar a falar com um IP de comando e controle ou começar a minerar criptomoedas (**CryptoCurrency attacks**), o GuardDuty grita.

O GuardDuty utiliza diversas fontes de dados da própria AWS.

**Fontes de Dados (Data Sources):** Ele não precisa instalar nada nos seus servidores. Ele analisa logs que já existem na AWS:
*   **AWS CloudTrail events:** Log de quem está fazendo o quê via API.
*   **VPC Flow Logs:** Registro do tráfego de rede.
*   **DNS Logs:** Para ver se seu servidor está tentando resolver domínios maliciosos.
*   **EKS Audit Logs:** Para monitorar seus clusters Kubernetes.

---

### Exemplos de detecção

O GuardDuty pode identificar:

- Tentativas de acesso usando credenciais comprometidas
- Comunicação com IPs maliciosos
- Instâncias EC2 realizando mineração de criptomoedas
- Tentativas de exfiltração de dados
- Escaneamentos suspeitos na rede
- Comportamentos incomuns de usuários IAM

---

### Exemplo prático

Imagine que uma EC2 normalmente acessa apenas um banco de dados interno.

De repente ela começa a:

- conectar em dezenas de IPs desconhecidos;
- enviar grande volume de dados para fora;
- comunicar-se com um servidor conhecido por hospedar malware.

O GuardDuty identifica esse comportamento anômalo e gera um **Finding**.

---

## 2. Amazon Inspector: O Auditor de Vulnerabilidades

Ele é um serviço automatizado de **gerenciamento de vulnerabilidades (Vulnerability Management).** 

Diferente do GuardDuty que caça ataques em tempo real, o **Amazon Inspector** foca em encontrar portas abertas e trincas na sua armadura. Ou seja, enquanto o ***GuardDuty*** procura ataques acontecendo agora, o ***Inspector*** procura falhas que **podem permitir um ataque no futuro**.

*   **O que ele escaneia:** Ele foca em três alvos principais:
    1.  **Instâncias EC2:** Olha o sistema operacional em busca de pacotes desatualizados e vulnerabilidades conhecidas (**CVEs**).
    2.  **Amazon ECR:** Escaneia imagens de contêiner assim que você faz o push.
    3.  **AWS Lambda:** Analisa o código das suas funções em busca de falhas.
*   **Ação:** Ele gera um relatório de descobertas (findings) com uma pontuação de risco para que você saiba o que consertar primeiro.

---

### O que ele procura?

Entre as principais verificações estão:

- CVEs (Common Vulnerabilities and Exposures)
- Pacotes desatualizados
- Bibliotecas vulneráveis
- Configurações inseguras
- Exposição indevida à Internet (Network Reachability)

---

### Exemplo prático

Uma instância EC2 possui:

- Ubuntu desatualizado;
- OpenSSL vulnerável;
- Apache com versão conhecida por possuir falhas críticas.

O Inspector identifica essas vulnerabilidades e gera recomendações para correção.

---

## 3. Duelo de Segurança: GuardDuty vs. Inspector

Bata o olho nesta tabela para não cair em pegadinha de cenário:

| Critério | Amazon GuardDuty | Amazon Inspector |
| :--- | :--- | :--- |
| **Foco Principal** | Detecção de ameaças (Threat Detection). | Gestão de vulnerabilidades (CVEs) e análise de software. |
| **Inteligência** | Baseado em Machine Learning e Anomalias. | Baseado em assinaturas de falhas conhecidas. |
| **Onde olha?** | Logs de rede e API (CloudTrail, VPC Flow). | Dentro do SO, código e pacotes. |
| **Instalação** | Sem agente (Agentless). | Pode exigir Agente SSM para scan profundo no EC2. |
| **Tempo** | Durante a execução | Antes da exploração |
| **Exemplo de Alerta** | "Instância fazendo mineração de Bitcoin". | "Versão do Apache está velha e vulnerável". |

---

### Fluxo Mental

~~~mermaid
flowchart LR

    A([🖥️ Infraestrutura AWS])

    B["📋 Amazon Inspector<br/>🔎 Procura vulnerabilidades"]

    C["🕵️ Amazon GuardDuty<br/>🚨 Detecta ameaças ativas"]

    A --> B --> C

    classDef infra fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef inspector fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef guard fill:#FDECEA,stroke:#D32F2F,stroke-width:2px;

    class A infra;
    class B inspector;
    class C guard;
~~~

---

## 4. Complementaridade em SecOps

Na prática de **SecOps (Security Operations)**, eles são os melhores amigos. O **Inspector** é preventivo: você usa ele para "fechar as janelas" e garantir que sua aplicação nasceu segura. O **GuardDuty** é detectivo: ele fica de olho se, mesmo com tudo fechado, alguém conseguiu entrar ou se um funcionário interno está fazendo bobagem. 

### Fluxo simplificado:

~~~mermaid
flowchart LR

    subgraph PREV["🛡️ Prevenção"]
        I["📋 Amazon Inspector"]
        V["🔍 Identifica vulnerabilidades"]
        C["🛠️ Corrigir vulnerabilidades"]

        I --> V --> C
    end

    subgraph DET["🚨 Detecção"]
        G["🕵️ Amazon GuardDuty"]
        M["📡 Monitoramento contínuo"]
        D["⚠️ Detecta ameaças reais"]

        G --> M --> D
    end

    C --> G

    classDef prev fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef det fill:#FDECEA,stroke:#D32F2F,stroke-width:2px;

    class I,V,C prev;
    class G,M,D det;
~~~

* Um reduz a superfície de ataque.
* O outro monitora continuamente caso algo consiga passar.

---

### Integração com AWS Security Hub

Em ambientes corporativos normalmente ambos enviam seus resultados para o **AWS Security Hub**.

---

#### Fluxo:

~~~mermaid
flowchart LR

    I["📋 Amazon Inspector"]
    G["🕵️ Amazon GuardDuty"]
    M["🔒 Outros serviços de segurança"]

    H["🛡️ AWS Security Hub"]

    D["📊 Painel unificado<br/>Alertas • Findings • Compliance"]

    I --> H
    G --> H
    M --> H

    H --> D

    classDef source fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef hub fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;
    classDef dash fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;

    class I,G,M source;
    class H hub;
    class D dash;
~~~

Assim o time de segurança consegue visualizar todos os achados em um único lugar.

---

## Casos clássicos de prova

### Cenário 1

> Quero descobrir se minhas instâncias possuem bibliotecas vulneráveis.

Resposta:

**Amazon Inspector**

---

### Cenário 2

> Quero detectar comportamento suspeito utilizando Machine Learning.

Resposta:

**Amazon GuardDuty**

---

### Cenário 3

> Minha EC2 começou a conversar com um servidor conhecido por distribuir malware.

Resposta:

**Amazon GuardDuty**

---

### Cenário 4

> Quero encontrar CVEs em imagens Docker armazenadas no Amazon ECR.

Resposta:

**Amazon Inspector**

---

### Cenário 5

> Quero saber quais servidores possuem pacotes desatualizados.

Resposta:

**Amazon Inspector**

---

## GuardDuty ≠ Macie

Outra pegadinha bastante comum.

Se a questão falar sobre:

- CPF
- Cartão de crédito
- Dados pessoais
- Dados sensíveis armazenados no S3

A resposta **não** é GuardDuty.

O serviço correto é o **Amazon Macie**, especializado em descoberta e classificação automática de dados sensíveis.

---

## Comparação Rápida

| Serviço | Especialidade |
|----------|---------------|
| **GuardDuty** | Detectar ameaças |
| **Inspector** | Encontrar vulnerabilidades |
| **Macie** | Descobrir dados sensíveis |
| **Security Hub** | Centralizar descobertas |

---

## Resumo para a prova

| Serviço | Palavra-chave |
|----------|---------------|
| GuardDuty | ***Threat Detection*** |
| GuardDuty | ***Machine Learning** |
| GuardDuty | ***Anomaly Detection** |
| GuardDuty | ***CloudTrail** |
| GuardDuty | ***VPC Flow Logs** |
| GuardDuty | ***DNS Logs** |
| GuardDuty | ***Findings** |
| Inspector | ***Vulnerability Assessment** |
| Inspector | ***CVE** |
| Inspector | ***Package Scan** |
| Inspector | ***EC2** |
| Inspector | ***Amazon ECR** |
| Inspector | ***AWS Lambda** |
| Inspector | ***Network Reachability** |

---

## Mnemônico

## GuardDuty → Guarda

> **GuardDuty "GUARDA" sua conta procurando ataques.**

Pense em:

- Hacker
- Malware
- IP malicioso
- Mineração
- Anomalias

---

## Inspector → Inspetor

> **Inspector "INSPECIONA" seu ambiente procurando falhas.**

Pense em:

- CVEs
- Pacotes
- Bibliotecas
- Vulnerabilidades
- Correções

---

## 🎯 Gatilho de Exame

Identifique o serviço pelas palavras-chave em inglês no enunciado:

*   **Amazon GuardDuty:** Pense em "Threat detection", "Machine Learning (ML) threat analysis", "Unusual account activity" e "Malicious activity".
*   **Amazon Inspector:** Pense em "Vulnerability management/assessment", "CVE scanning", "Software vulnerabilities" e "Package scan".
*   **Network Reachability:** Recurso do Inspector para ver se seu servidor está exposto à internet de forma não intencional.

> **Sinal de Alerta:** Se a questão falar em descobrir dados sensíveis como CPF ou cartão de crédito em um bucket S3, a resposta NÃO é nenhum desses dois; a resposta é **Amazon Macie**. GuardDuty e Inspector não olham o conteúdo dos seus arquivos no S3.

Se aparecer... use esses gatilhos rapidos:

| Enunciado | Resposta |
|------------|----------|
| Threat Detection | ***GuardDuty*** |
| Machine Learning | ***GuardDuty*** |
| Suspicious Activity | ***GuardDuty*** |
| CryptoCurrency Attack | ***GuardDuty*** |
| Malicious IP | ***GuardDuty*** |
| CloudTrail Analysis | ***GuardDuty*** |
| Vulnerability Scan | ***Inspector*** |
| CVE | ***Inspector*** |
| Package Vulnerability | ***Inspector*** |
| ECR Image Scan | ***Inspector*** |
| Lambda Vulnerability | ***Inspector*** |
| Network Reachability | ***Inspector*** |

---

> **💡 Dica de Ouro:** Pense sempre assim: **"O problema já está acontecendo?" → GuardDuty. "Quero evitar que aconteça?" → Inspector. "Quero encontrar dados sensíveis?" → Macie.**

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 2: Auditoria e Logs: AWS CloudTrail (Quem fez o quê?)](06-auditoria-e-logs-cloudtrail-quem-fez-o-que.md)
* [➡️ Módulo 2: Privacidade de Dados: Amazon Macie e Proteção de PII](08-privacidade-de-dados-amazon-macie-pii.md)

---
---