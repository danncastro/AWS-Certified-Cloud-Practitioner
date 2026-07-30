# Central de Segurança: AWS Security Hub

Gerenciar a segurança de um ambiente AWS pode rapidamente se tornar um desafio. Cada serviço de segurança gera seus próprios alertas, possui seu próprio console e apresenta informações de maneiras diferentes.

O **AWS Security Hub** resolve esse problema funcionando como uma central única de segurança (**single pane of glass**), reunindo os principais alertas da conta em um único dashboard.

Além de centralizar os findings de diversos serviços, ele também avalia continuamente se o ambiente segue as boas práticas de segurança recomendadas pela AWS e pelos principais padrões do mercado.

---

## 1. O que é o AWS Security Hub?

O **AWS Security Hub** é um serviço de **Cloud Security Posture Management (CSPM)** que centraliza informações de segurança provenientes de diversos serviços AWS e soluções de parceiros.

Em vez de acessar individualmente cada ferramenta para verificar possíveis problemas, o Security Hub reúne todos os findings em um único painel, facilitando a visualização, priorização e investigação de incidentes.

Entre os serviços integrados automaticamente estão:

* **Amazon GuardDuty:** Detecção inteligente de ameaças e atividades suspeitas.
* **Amazon Inspector:** Descoberta de vulnerabilidades em EC2, ECR e Lambda.
* **Amazon Macie:** Identificação de dados sensíveis (PII) armazenados no Amazon S3.
* **IAM Access Analyzer:** Detecção de acessos externos não intencionais.
* **AWS Systems Manager:** Informações sobre conformidade de patches e configurações.

Isso permite que equipes de segurança tenham uma visão consolidada da postura de segurança da conta ou até mesmo de toda uma organização utilizando AWS Organizations.

---

### Fluxo Simplificado

~~~mermaid
graph TD
    GD[GuardDuty] --> SH{AWS Security Hub}
    Insp[Inspector] --> SH
    Macie[Macie] --> SH
    IAM[IAM Access Analyzer] --> SH
    SSM[Systems Manager] --> SH
    SH --> Dashboard[Dashboard Centralizado]
~~~

---

## 2. Verificações de Conformidade (Security Standards)

Além de consolidar alertas, o Security Hub também executa verificações automáticas de conformidade (*Security Standards*).

Essas verificações analisam continuamente os recursos da conta para identificar configurações que não seguem boas práticas de segurança ou requisitos regulatórios.

Os padrões mais cobrados na prova são:

### CIS AWS Foundations Benchmark

Conjunto de controles de segurança desenvolvido pelo **Center for Internet Security (CIS)**.

É um dos benchmarks mais utilizados para avaliar se uma conta AWS está configurada de forma segura.

---

### AWS Foundational Security Best Practices (FSBP)

Conjunto de boas práticas desenvolvido pela própria AWS.

Avalia centenas de controles relacionados a serviços como IAM, S3, EC2, CloudTrail, Config, entre outros.

É um dos padrões mais utilizados no dia a dia.

---

### PCI DSS

Voltado para empresas que armazenam, processam ou transmitem dados de cartões de crédito.

O Security Hub ajuda a identificar recursos que não atendem aos requisitos desse padrão.

---

### Requisito Técnico

Para que boa parte dessas verificações funcione corretamente, o **AWS Config** precisa estar habilitado, já que é ele quem coleta o estado de configuração dos recursos da conta.

---

## 3. Pontuação de Segurança (Security Score)

Para facilitar a análise da postura geral do ambiente, o Security Hub calcula automaticamente uma **Pontuação de Segurança (Security Score)**.

Essa pontuação representa o percentual de controles aprovados em relação aos controles avaliados pelos padrões habilitados.

Quanto maior a pontuação, maior é o nível de conformidade do ambiente com as boas práticas de segurança.

Quando existem problemas, o Security Hub mostra exatamente:

* quais controles falharam;
* quais recursos foram afetados;
* o nível de severidade (*Critical, High, Medium ou Low*);
* recomendações para correção.

Isso permite que a equipe priorize primeiro os riscos mais críticos, em vez de tentar corrigir tudo ao mesmo tempo.

---

### Exemplo

Imagine que uma empresa possui centenas de recursos AWS.

O Security Hub pode identificar que:

- um bucket S3 está público;
- uma Role do IAM possui permissões excessivas;
- uma instância EC2 possui vulnerabilidades encontradas pelo Inspector;
- o GuardDuty detectou comunicação com um IP malicioso.

Em vez de consultar quatro consoles diferentes, todos esses findings aparecem centralizados no Security Hub.

---

## 4. A Diferença Crucial na Prova

Essa é uma das pegadinhas mais comuns da CLF-C02.

Os serviços **GuardDuty**, **Inspector** e **Macie** são responsáveis por identificar problemas específicos.

O **Security Hub não faz essa detecção diretamente**.

Seu papel é reunir todos esses findings, organizá-los em um único dashboard e fornecer uma visão consolidada da postura de segurança da conta.

Uma forma simples de memorizar é:

| Serviço | Responsabilidade |
|----------|------------------|
| GuardDuty | Detecta ameaças e atividades suspeitas |
| Inspector | Descobre vulnerabilidades |
| Macie | Identifica dados sensíveis (PII) |
| Security Hub | Centraliza findings e avalia conformidade |

---

## Casos Clássicos de Prova

### Cenário 1

> Quero visualizar todos os alertas de segurança da conta em um único lugar.

**Resposta:** AWS Security Hub.

---

### Cenário 2

> Preciso acompanhar a postura geral de segurança da organização.

**Resposta:** AWS Security Hub.

---

### Cenário 3

> Quero verificar se minha conta atende ao CIS Benchmark.

**Resposta:** AWS Security Hub.

---

### Cenário 4

> Preciso descobrir quem gerou determinado finding.

**Resposta:** O finding provavelmente veio do GuardDuty, Inspector ou Macie, mas será visualizado pelo Security Hub.

---

## Security Hub vs Outros Serviços

| Serviço | Especialidade |
|----------|---------------|
| AWS Security Hub | Centraliza findings e monitora conformidade |
| Amazon GuardDuty | Detecta ameaças e comportamentos suspeitos |
| Amazon Inspector | Identifica vulnerabilidades |
| Amazon Macie | Descobre dados sensíveis no S3 |
| AWS Config | Avalia configurações dos recursos |
| Amazon Detective | Investiga incidentes de segurança |

---

## O que o Security Hub NÃO faz?

O Security Hub não:

- substitui o GuardDuty;
- substitui o Inspector;
- substitui o Macie;
- executa scans de vulnerabilidades;
- detecta ataques diretamente.

Seu papel é consolidar informações de segurança e fornecer uma visão centralizada do ambiente.

---

## Resumo Rápido

| Recurso | AWS Security Hub |
|----------|------------------|
| Centraliza findings | ✅ |
| Dashboard único | ✅ |
| Security Score | ✅ |
| CIS Benchmark | ✅ |
| AWS Foundational Security Best Practices | ✅ |
| PCI DSS | ✅ |
| Integra GuardDuty | ✅ |
| Integra Inspector | ✅ |
| Integra Macie | ✅ |
| Detecta ameaças diretamente | ❌ |
| Escaneia vulnerabilidades | ❌ |

---

## Mnemônico

### Security Hub → Hub de Segurança

Sempre associe:

**Security Hub = Central de Segurança**

Ele:

- reúne findings;
- centraliza dashboards;
- calcula Security Score;
- verifica conformidade;
- facilita priorização de riscos.

---

## 🎯 Gatilhos de Exame

Se aparecer...

| Enunciado | Resposta |
|------------|----------|
| Centralized security findings | AWS Security Hub |
| Single pane of glass | AWS Security Hub |
| Security Score | AWS Security Hub |
| CIS Benchmark | AWS Security Hub |
| AWS Foundational Security Best Practices | AWS Security Hub |
| Cloud Security Posture Management (CSPM) | AWS Security Hub |
| Consolidated security dashboard | AWS Security Hub |
| Compliance checks | AWS Security Hub |

---

## Pegadinhas da Prova

| Se a questão perguntar... | Resposta |
|----------------------------|----------|
| Quem detecta ameaças? | GuardDuty |
| Quem encontra vulnerabilidades? | Inspector |
| Quem descobre PII no S3? | Macie |
| Quem centraliza todos os findings? | AWS Security Hub |
| Quem calcula o Security Score? | AWS Security Hub |
| Quem investiga a causa raiz de um incidente? | Amazon Detective |

---

> **💡 Dica de Ouro:** Pense na seguinte sequência: **GuardDuty, Inspector e Macie encontram os problemas. O Security Hub organiza tudo em um único painel, calcula a postura de segurança e ajuda a priorizar as correções.**

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Conformidade e Relatórios: AWS Artifact](09-conformidade-e-relatorios-aws-artifact.md)
* [➡️ Tabela IAM User vs Group vs Role](11-tabela-iam-user-vs-group-vs-role.md)

---
---