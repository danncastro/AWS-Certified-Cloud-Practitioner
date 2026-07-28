# 🛡️ Proteção contra DDoS: AWS Shield e AWS WAF

A internet é um lugar hostil. Se você coloca um app no ar sem proteção de borda, é só questão de tempo até alguém tentar injetar código no seu banco ou derrubar seu serviço com um tráfego massivo. 

Na AWS, dois serviços trabalham juntos para proteger aplicações:

- **AWS WAF (Web Application Firewall)** → Protege contra ataques na aplicação (Camada 7).
- **AWS Shield** → Protege contra ataques DDoS (Camadas 3 e 4).

---

## 1. AWS WAF: O Segurança do Tráfego Web (Layer 7)

O **AWS WAF (Web Application Firewall)** é o serviço que olha o que está escrito dentro dos pacotes HTTP/HTTPS  antes que elas cheguem à aplicação. Ele opera na **Camada 7 (Application Layer)** do modelo OSI.

*   **O que ele faz:** Filtra requisições maliciosas antes mesmo delas tocarem o seu servidor ou banco de dados.
*   **Ataques Clássicos:** Protege contra vulnerabilidades comuns do **OWASP Top 10**, focando principalmente em:
    *   **SQL Injection (SQLi):** Tentativa de enfiar código malicioso nos campos de formulário para extrair dados do banco.
    *   **Cross-Site Scripting (XSS):** Injeção de scripts maliciosos para serem executados no navegador de outros usuários.
    *   **Outros exemplos:** 
        - Bots maliciosos
        - IPs suspeitos
        - Países específicos
        - Requisições excessivas (Rate Limiting)

---

### SQL Injection

Nesse tipo de ataque, o invasor tenta inserir comandos SQL dentro dos campos da aplicação para acessar ou modificar informações do banco de dados.

Exemplo:

~~~sql
' OR 1=1 --
~~~

O ***AWS WAF*** consegue identificar esse padrão e bloquear a requisição antes que ela alcance a aplicação.

---

### Cross-Site Scripting (XSS)

No ataque XSS, o invasor tenta inserir scripts JavaScript maliciosos para serem executados no navegador de outros usuários.

Exemplo:

~~~html
<script>alert("Hackeado")</script>
~~~

O WAF identifica esse comportamento e impede que o script seja processado.

---

### Como o WAF funciona?

Você configura uma **Web ACL (Web Access Control List)** com regras customizáveis. Uma *Web ACL* pode conter diversas regras, como:

- Permitir determinados IPs.
- Bloquear IPs específicos.
- Filtrar por cabeçalhos (headers)
- Restringir o acesso por países (Geo-match).
- Limitar número de requisições (Rate Limit).
- Detectar SQL Injection.
- Detectar XSS.

---

### Recursos compatíveis com WAF

O *AWS WAF* pode proteger serviços como:

- Amazon CloudFront
- Application Load Balancer (ALB)
- Amazon API Gateway
- AWS AppSync
- Amazon Cognito

---

## 2. AWS Shield: O Escudo contra DDoS (Layer 3 e 4)

Enquanto o WAF analisa a "conversa" (conteúdo), o **AWS Shield** foca no "volume". O objetivo dele é a mitigação de ataques de **DDoS (Distributed Denial of Service)**, que tentam tirar seu sistema do ar sobrecarregando a rede.

O Shield atua principalmente nas:

- Camada 3 (Network)
- Camada 4 (Transport)

---

### O que é um ataque DDoS?

**DDoS (Distributed Denial of Service)** é um ataque onde milhares ou milhões de dispositivos enviam tráfego simultaneamente para um serviço.

O objetivo é:

- Consumir largura de banda.
- Esgotar recursos computacionais.
- Tornar a aplicação indisponível.

Existem dois níveis que você precisa diferenciar para a prova:

---

### AWS Shield Standard
*   **Automático e Gratuito:** Já vem ativado por padrão para todos os clientes AWS sem custo adicional.
*   **Foco:** Protege contra os ataques de DDoS mais comuns e frequentes na camada de rede (como SYN/UDP floods).

---

### AWS Shield Advanced
O **AWS Shield Advanced** é a versão premium do serviço. Além da proteção contra DDoS, oferece recursos adicionais.

*   **Proteção de Elite (Serviço Pago):** Oferece uma camada muito mais robusta de defesa e exige um compromisso financeiro mensal.
*   **DDoS Response Team (DRT):** Clientes recebem acesso 24/7 a um time de especialistas da AWS para ajudar a mitigar ataques complexos em tempo real.
*   **Proteção Financeira (Cost Protection):** Protege sua empresa contra picos de cobrança. Se um ataque DDoS fizer seu Auto Scaling "explodir" o número de instâncias para aguentar a carga, a AWS reembolsa esses custos.
* **Monitoramento Avançado:** O serviço fornece métricas detalhadas sobre ataques e mecanismos adicionais de mitigação.


### Shield Standard × Shield Advanced

| Característica | Shield Standard | Shield Advanced |
|----------------|-----------------|-----------------|
| Gratuito | ✅ | ❌ |
| Ativado automaticamente | ✅ | ❌ |
| Proteção básica contra DDoS | ✅ | ✅ |
| DDoS Response Team (DRT) | ❌ | ✅ |
| Cost Protection | ❌ | ✅ |
| Monitoramento avançado | ❌ | ✅ |

---

## 3. Quem é Quem: Tabela de Decisão Rápida

Use esta tabela para não travar nos cenários situacionais:

| Requisito do Enunciado | Resposta Correta | Motivo Técnico |
| :--- | :--- | :--- |
| Bloquear um IP malicioso ou range de IPs | **AWS WAF** | Controle granular via Web ACL. |
| Bloquear SQL Injection ou XSS | **AWS WAF** | Inspeção de pacotes na Camada 7. |
| Bloquear países | **AWS WAF** | Bloqueio via GeoIP |
| Proteção contra ataques volumétricos massivos | **AWS Shield** | Focado em mitigação de DDoS. |
| Preciso de suporte especializado 24/7 (DRT) | **Shield Advanced** | Acesso ao time de resposta a DDoS. |
| Reembolso por picos de custo durante ataque | **Shield Advanced** | Recurso exclusivo de proteção de custos. |

---

### AWS WAF × AWS Shield

| Característica | AWS WAF | AWS Shield |
|----------------|----------|-------------|
| Protege contra SQL Injection | ✅ | ❌ |
| Protege contra XSS | ✅ | ❌ |
| Protege contra DDoS | ❌ | ✅ |
| Analisa conteúdo HTTP | ✅ | ❌ |
| Atua na Camada 7 | ✅ | ❌ |
| Atua nas Camadas 3 e 4 | ❌ | ✅ |

---

# WAF + Shield

Na prática, os dois serviços costumam trabalhar juntos.

Fluxo simplificado:

~~~mermaid
flowchart LR

    INTERNET([🌐 Internet])

    SHIELD["🛡️ AWS Shield"]
    WAF["🔥 AWS WAF"]

    subgraph EDGE["Camada de Entrada"]
        CF["🌍 CloudFront"]
        ALB["⚖️ Application Load Balancer"]
        API["🚪 API Gateway"]
    end

    APP["🖥️ Aplicação"]

    INTERNET --> SHIELD
    SHIELD --> WAF

    WAF --> CF
    WAF --> ALB
    WAF --> API

    CF --> APP
    ALB --> APP
    API --> APP
~~~

O Shield reduz o impacto dos ataques volumétricos.

O WAF bloqueia requisições maliciosas que conseguem chegar até a aplicação.

---

## 🎯 Gatilho de Exame

Mapeie esses termos em inglês para identificar a resposta certa na hora H:

| Termo | Significado |
|--------|-------------|
| AWS WAF | Firewall de aplicação |
| Web ACL | Conjunto de regras do WAF |
| Layer 7 | Camada de aplicação |
| SQL Injection | AWS WAF |
| Cross-Site Scripting (XSS) | AWS WAF |
| Rate Limiting | AWS WAF |
| AWS Shield | Proteção contra DDoS |
| DDoS Mitigation | AWS Shield |
| Shield Standard | Gratuito e automático |
| Shield Advanced | Proteção premium |
| DDoS Response Team (DRT) | Especialistas da AWS |
| Cost Protection | Reembolso de custos durante ataques |

> **Pegadinha de Simulado:** O WAF pode ser implantado no **Application Load Balancer (ALB)**, **Amazon API Gateway** e **Amazon CloudFront**. Se a questão falar em proteger um **Network Load Balancer (NLB)** contra DDoS massivo, o foco é **Shield**, pois o WAF não olha Camada 4.

---

### ⚠️ Sinais de atenção

- **WAF protege aplicações; Shield protege infraestrutura de rede.**
- **SQL Injection e XSS sempre apontam para o AWS WAF.**
- **Ataques DDoS sempre apontam para o AWS Shield.**
- O **Shield Standard** já está habilitado automaticamente para todos os clientes AWS.
- O **Shield Advanced** oferece **DRT (DDoS Response Team)** e **Cost Protection**.
- O WAF pode ser associado ao **CloudFront**, **Application Load Balancer (ALB)**, **API Gateway**, **AppSync** e **Amazon Cognito**.
- O WAF **não protege** diretamente contra ataques volumétricos de rede (Camadas 3 e 4); essa é a função do **AWS Shield**.

---

* [🏠 Menu Principal](../README.md)
* [⬅️ Criptografia: KMS vs. CloudHSM e a Regra de Ouro](04-criptografia-kms-vs-cloudhsm-golden-rule.md)
* [➡️ Criptografia: KMS vs. CloudHSM e a Regra de Ouro](03-protecao-contra-ddos-shield-e-waf.md)

---
---