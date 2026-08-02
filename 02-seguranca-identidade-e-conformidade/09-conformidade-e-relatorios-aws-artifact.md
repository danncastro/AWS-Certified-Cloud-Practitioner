# Conformidade e Relatórios: AWS Artifact

Quando a auditoria bate na porta da empresa perguntando se a nuvem é segura de verdade, você não precisa entrar em pânico nem tentar tirar foto dos servidores da Amazon.

Na AWS, segurança não significa apenas proteger recursos. Em ambientes corporativos também é preciso **comprovar** que a infraestrutura atende padrões internacionais de conformidade.

É exatamente esse o papel do **AWS Artifact**.

O Artifact é um portal gratuito de autosserviço que disponibiliza documentos oficiais de auditoria, certificações e acordos legais relacionados aos serviços da AWS.

Em vez de abrir chamados para solicitar relatórios, basta acessar o console e fazer o download.

---

## 1. O que é o AWS Artifact?

O **AWS Artifact** é um portal de autosserviço que fornece acesso sob demanda a documentos de conformidade da AWS. É aqui que a Amazon prova que segue as regras do jogo. Em vez de abrir um chamado e esperar dias, você entra no console, escolhe o documento e baixa na hora.

Ele serve para:
*   Apoiar suas auditorias internas e externas.
*   Provar para reguladores que a infraestrutura da AWS é segura (Demonstrar conformidade regulatória).
*   Aceitar termos legais específicos entre sua empresa e a AWS.
*   Obter certificações da infraestrutura AWS
*   Revisar contratos legais
*   Atender requisitos de órgãos reguladores

Ele permite que empresas obtenham rapidamente evidências de que a infraestrutura da AWS atende diversos padrões internacionais.

É muito utilizado por equipes de:

- Auditoria
- Segurança
- Compliance
- Governança
- Jurídico

---

## 2. Os Dois Pilares do AWS Artifact

Para a prova CLF-C02, você precisa distinguir os dois recursos principais que moram dentro desse portal:

---

### AWS Artifact Reports (Relatórios)
Aqui você baixa os laudos técnicos emitidos por auditores externos e independentes que entraram nos data centers da AWS e validaram tudo.
*   **Exemplos clássicos:** Relatórios **SOC** (1, 2 e 3), certificações **ISO** (como a 27001), laudos de conformidade com **PCI-DSS** (para quem mexe com cartão de crédito) e **FedRAMP**.
*   **Uso:** Você entrega esses PDFs para o seu auditor para comprovar que a base onde seu sistema roda é certificada.

---

#### Exemplo

Imagine que um auditor pergunta:

> "Como vocês comprovam que a infraestrutura onde o sistema roda segue padrões internacionais de segurança?"

Você simplesmente baixa o relatório correspondente no AWS Artifact.

---

### AWS Artifact Agreements (Acordos)
Aqui é onde você gerencia o "jurídico" da sua conta. Permite revisar e aceitar acordos em nível de conta ou para toda a sua organização no AWS Organizations.
*   **BAA (Business Associate Addendum):** Essencial se você trabalha com dados de saúde nos EUA (**HIPAA**). Sem assinar isso no Artifact, você não pode legalmente processar dados de saúde protegidos.
*   **NDA (Nondisclosure Agreements):** Contratos de confidencialidade padrão.

---

#### Exemplo

Uma empresa da área de saúde precisa atender aos requisitos da HIPAA.

Antes de armazenar dados médicos na AWS, ela deve aceitar o **Business Associate Addendum (BAA)** através do AWS Artifact.

---

### Artifact Reports vs Artifact Agreements

| Recurso | Objetivo |
|----------|----------|
| Artifact Reports | Download de relatórios e certificações |
| Artifact Agreements | Aceitar contratos e acordos legais |

---

### Principais Certificações

A CLF-C02 costuma citar algumas certificações importantes.

#### SOC

Os relatórios SOC demonstram controles relacionados à segurança, disponibilidade e processamento.

Tipos comuns:

- SOC 1
- SOC 2
- SOC 3

---

#### ISO

Certificações internacionais relacionadas à gestão da segurança da informação.

Exemplo:

- ISO 27001

---

#### PCI DSS

Voltada para empresas que armazenam ou processam dados de cartões de crédito.

---

#### HIPAA

Norma norte-americana relacionada à proteção de dados de saúde.

Para utilizá-la na AWS normalmente é necessário aceitar o **BAA** pelo Artifact.

---

## 3. Conexão com o Modelo de Responsabilidade Compartilhada

Lembra do mantra: a AWS cuida da segurança **DA** nuvem (*Security OF the Cloud*). 

Como você garante que ela está fazendo o trabalho dela na infraestrutura física, energia e rede? Através do **AWS Artifact**. Ele é a ferramenta que materializa a responsabilidade da AWS. Os relatórios disponíveis lá são a evidência física de que a AWS cumpre a parte dela no modelo compartilhado.

O ***AWS Artifact*** fornece justamente as evidências de que a AWS está cumprindo sua parte.

Exemplos:

- Segurança física
- Data centers
- Energia
- Rede
- Hardware

Tudo isso pode ser comprovado através dos relatórios disponíveis no Artifact.

---

### Fluxo Simplificado

~~~mermaid
flowchart TD

    A["📝 Auditoria"]

    ART["📄 AWS Artifact"]

    A --> ART

    subgraph REP["📚 Reports"]
        SOC["SOC"]
        ISO["ISO"]
        PCI["PCI DSS"]
        FED["FedRAMP"]
    end

    subgraph AGR["🤝 Agreements"]
        BAA["BAA"]
        NDA["NDA"]
        OUT["Outros contratos"]
    end

    ART --> REP
    ART --> AGR
~~~

---

## 4. Casos clássicos de prova

### Cenário 1

> Preciso baixar um relatório SOC 2.

Resposta:

**AWS Artifact**

---

### Cenário 2

> Quero obter a certificação ISO 27001 da infraestrutura AWS.

Resposta:

**AWS Artifact**

---

### Cenário 3

> Preciso aceitar o Business Associate Addendum (BAA).

Resposta:

**AWS Artifact**

---

### Cenário 4

> O auditor pediu evidências de conformidade da infraestrutura AWS.

Resposta:

**AWS Artifact**

---

### Cenário 5

> Quero verificar se minha VPC está fora de conformidade.

Resposta:

**Não é o AWS Artifact.**

Serviços como **AWS Config** ou **AWS Audit Manager** são mais adequados para avaliar a configuração da sua própria infraestrutura.

---

### AWS Artifact vs Outros Serviços

Essa comparação aparece bastante na prova.

| Serviço | Especialidade |
|----------|---------------|
| AWS Artifact | Relatórios de compliance e acordos legais |
| AWS Config | Avaliar conformidade da configuração dos recursos |
| AWS Audit Manager | Automatizar evidências para auditorias |
| AWS CloudTrail | Auditoria de chamadas de API |
| AWS Security Hub | Centralizar Findings de segurança |

---

### O que o AWS Artifact NÃO faz?

O Artifact não:

- monitora recursos;
- verifica vulnerabilidades;
- detecta ataques;
- gera métricas;
- audita sua aplicação.

Seu papel é disponibilizar **documentação oficial** sobre a conformidade da infraestrutura AWS.

---

### Resumo Rápido

| Recurso | AWS Artifact |
|----------|--------------|
| Download de SOC | ✅ |
| Download de ISO | ✅ |
| Download de PCI DSS | ✅ |
| FedRAMP | ✅ |
| Agreements | ✅ |
| Business Associate Addendum (BAA) | ✅ |
| NDA | ✅ |
| Compliance Documentation | ✅ |
| Monitorar infraestrutura | ❌ |
| Detectar vulnerabilidades | ❌ |

---

## Mnemônico

### Artifact → Arquivos da Auditoria

Sempre associe:

**Artifact = Arquivos Oficiais**

Ele guarda:

- Certificações
- Relatórios
- Evidências
- Contratos
- Compliance

---

### Gatilho Imbatível de Prova

Não perca tempo lendo o enunciado três vezes. Se a pergunta disser:
*   *"Onde baixar relatórios de auditoria SOC ou PCI da AWS?"* ➔ **AWS Artifact**.
*   *"Onde aceitar um contrato BAA para conformidade HIPAA?"* ➔ **AWS Artifact**.
*   *"Onde obter evidências de auditoria de terceiros sobre a infraestrutura AWS?"* ➔ **AWS Artifact**.

---

## 🎯 Gatilho de Exame

Mapeie estes termos em inglês para não dar branco na hora H:

*   **AWS Artifact:** Portal central de documentos de conformidade.
*   **AWS Artifact Reports:** Download de laudos de auditoria de terceiros.
*   **AWS Artifact Agreements:** Revisão e aceitação de acordos legais/regulatórios.
*   **On-demand compliance documentation:** O propósito central do serviço.
*   **Third-party audit reports:** Evidência técnica da segurança da AWS.
*   **SOC / PCI-DSS / ISO compliance:** Padrões industriais cujos laudos estão no portal.
*   **Business Associate Addendum (BAA):** Termo jurídico para conformidade com leis de saúde (HIPAA).

> **Sinal de Alerta:** O AWS Artifact fornece documentos sobre a **infraestrutura da AWS**. Ele NÃO gera relatórios sobre a conformidade do seu código ou da sua aplicação. Para monitorar se a *sua* configuração está correta, você usaria o **AWS Config** ou o **AWS Audit Manager**.

# Gatilhos de Exame

Se aparecer...

| Enunciado | Resposta |
|------------|----------|
| Compliance Documentation | AWS Artifact |
| Third-party Audit Reports | AWS Artifact |
| SOC Reports | AWS Artifact |
| ISO Certification | AWS Artifact |
| PCI DSS Reports | AWS Artifact |
| FedRAMP | AWS Artifact |
| AWS Artifact Reports | AWS Artifact |
| AWS Artifact Agreements | AWS Artifact |
| Business Associate Addendum (BAA) | AWS Artifact |
| HIPAA Agreement | AWS Artifact |

---

# Pegadinhas da Prova

| Se a questão perguntar... | Resposta |
|----------------------------|----------|
| Quem fez determinada ação? | CloudTrail |
| Minha infraestrutura segue boas práticas? | AWS Config / Audit Manager |
| Onde baixar relatórios SOC ou ISO? | AWS Artifact |
| Onde aceitar o BAA? | AWS Artifact |
| Onde verificar vulnerabilidades? | Amazon Inspector |
| Onde detectar ataques? | Amazon GuardDuty |

---

> **💡 Dica de Ouro:** Pense sempre assim: **"Preciso de um documento oficial da AWS?" → AWS Artifact. "Preciso verificar a conformidade da minha configuração?" → AWS Config ou AWS Audit Manager. "Preciso investigar ações na conta?" → AWS CloudTrail.**

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 2: Privacidade de Dados: Amazon Macie e Proteção de PII](08-privacidade-de-dados-amazon-macie-pii.md)
* [➡️ Módulo 2: Central de segurança (Security Hub)](10-central-de-seguranca-security-hub.md)

---
---