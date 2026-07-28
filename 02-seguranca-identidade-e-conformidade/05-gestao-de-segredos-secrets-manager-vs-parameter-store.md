# Gestão de Segredos: Secrets Manager vs. Parameter Store

Um dos erros mais cabulosos que um dev pode cometer é deixar senhas de banco de dados, chaves de API ou tokens de terceiros escritos diretamente no código (**hardcoded**). Se esse código cai num repositório público ou é acessado por alguém não autorizado, a sua infraestrutura vira um parque de diversões para hackers.

A AWS oferece dois serviços para resolver esse problema de forma segura:

- **AWS Secrets Manager**
- **AWS Systems Manager Parameter Store**

Embora ambos possam armazenar informações sensíveis, eles possuem objetivos diferentes e essa diferença é bastante cobrada na prova da **AWS Certified Cloud Practitioner (CLF-C02)**.

---

## 1. O Perigo das Hardcoded Credentials

Escrever segredos no código-fonte ou em arquivos de configuração (`.env`, `.ini`, `config.json`) dentro do servidor é pedir para ter problemas. 

---

### Riscos

- Vazamento de senhas caso o código seja exposto.
- Dificuldade para alterar credenciais.
- Falta de auditoria sobre quem acessou o segredo.
- Necessidade de realizar novo deploy sempre que uma senha mudar.

A melhor prática é armazenar essas informações em um serviço seguro e recuperá-las dinamicamente utilizando SDKs, APIs ou a AWS CLI.

Esse modelo segue o **Princípio do Menor Privilégio (Least Privilege)** e reduz significativamente o risco de exposição de credenciais.

---

## 2. AWS Secrets Manager: O Especialista em Rotação

O **AWS Secrets Manager** é o serviço "premium" desenhado especificamente para segredos que precisam de um ciclo de vida rigoroso. Ele armazena, gerencia e recupera credenciais de forma criptografada (integrado ao KMS).

---

### O que pode armazenar?

- Senhas de banco de dados
- API Keys
- Tokens OAuth
- Chaves de aplicações
- Credenciais de terceiros

---

### Principal diferencial: Rotação Automática

Este é o maior gatilho da prova.

O Secrets Manager consegue alterar automaticamente credenciais sem que a aplicação precise ser modificada.

Na maioria dos casos, a rotação utiliza uma função **AWS Lambda** responsável por:

1. Alterar a senha no banco de dados.
2. Atualizar o segredo armazenado.
3. Manter a aplicação funcionando utilizando a nova credencial.

#### Como funciona a rotação: 
Ele usa uma função AWS Lambda por trás dos panos para ir no banco, mudar a senha e atualizar o valor dentro do Secrets Manager

Esse recurso possui integração nativa com serviços como:

- Amazon RDS
- Amazon Aurora
- Amazon Redshift
- Amazon DocumentDB

---

~~~mermaid
flowchart LR

App["Aplicação"]

SM["AWS Secrets Manager"]

Lambda["AWS Lambda"]

DB["Amazon RDS"]

App --> SM

SM --> Lambda

Lambda --> DB
~~~

---


---

## 3. AWS Systems Manager Parameter Store (SSM Parameter Store)

O **SSM Parameter Store** é o "canivete suíço" para configurações de sistema. Ele serve para guardar strings simples, URLs de conexão, caminhos de pastas ou até chaves criptografadas (usando o tipo **SecureString**).

---

### Exemplos de parâmetros

- URLs
- Endpoints
- Configurações da aplicação
- Feature Flags
- Caminhos de diretórios
- Variáveis de ambiente

---

### Organização Hierárquica

Uma das grandes vantagens do Parameter Store é a organização em formato de árvore.

Exemplo:

~~~text
/prod/api/database/host
/prod/api/database/user
/prod/api/database/password
/dev/api/database/password
~~~

Isso facilita bastante o gerenciamento de ambientes diferentes.

---

### Custo-Benefício:

O Parameter Store Possui uma camada gratuita (**Standard parameters**) que permite armazenar até 10.000 parâmetros por conta, bastante utilizada para configurações de aplicações.

Por isso, costuma ser a opção mais econômica quando não existe necessidade de rotação automática.

---

### Limitação Importante

O **Parameter Store** **não possui rotação automática nativa**.

É possível implementar uma solução utilizando Lambda, EventBridge e outras automações, mas isso precisa ser construído pelo cliente.

Já o **Secrets Manager** oferece esse recurso pronto.

---

## 4. Tabela Comparativa de Decisão (Gatilho de Prova)

Bata o olho nesta tabela para decidir qual serviço o enunciado da questão está pedindo:

| Requisito do Enunciado | AWS Secrets Manager | SSM Parameter Store |
| :--- | :--- | :--- |
| **O que armazena?** | Segredos críticos (senhas, API Keys). | Configurações gerais e strings. |
| **Rotação Automática?** | **Sim** (Nativa para RDS/Redshift). | Não (Somente via lógica manual). |
| **Custo** | Pago por segredo/mês + chamadas API. | Camada gratuita disponível (Standard). |
| **Uso Principal** | Gerenciar ciclo de vida de credenciais. | Gerenciar configurações hierárquicas. |
| **Criptografia** | Sempre criptografado via KMS. | Opcional (via tipo SecureString). |

---

### Comparação Rápida

| Característica | AWS Secrets Manager | SSM Parameter Store |
|---------------|---------------------|---------------------|
| Armazena segredos | ✅ | ✅ |
| Armazena configurações gerais | ⚠️ Pode | ✅ |
| Rotação automática | ✅ | ❌ |
| Integração nativa com RDS | ✅ | ❌ |
| Utiliza KMS | ✅ | ✅ (SecureString) |
| Organização hierárquica | Limitada | ✅ |
| Camada gratuita | ❌ | ✅ (Standard Tier) |
| Melhor para senhas e API Keys | ✅ | ⚠️ Apenas quando não há necessidade de rotação |

---

## 6. Quando utilizar cada um?

### Utilize o AWS Secrets Manager quando:

- precisar armazenar senhas;
- possuir credenciais críticas;
- precisar de rotação automática;
- utilizar bancos gerenciados pela AWS;
- desejar menor esforço operacional.

---

### Utilize o SSM Parameter Store quando:

- armazenar configurações da aplicação;
- organizar parâmetros por ambiente;
- reduzir custos;
- guardar dados utilizando SecureString sem necessidade de rotação automática.

---

## 🎯 Gatilho de Exame

Associe estes termos aos respectivos serviços:

*   **Hardcoded credentials:** Problema que ambos os serviços resolvem ao centralizar segredos.
*   **Automatic rotation of secrets:** → **AWS Secrets Manager**.
*   **SecureString parameter:** Recurso do **SSM Parameter Store** para guardar dados sensíveis com KMS.
*   **Cost-effective configuration storage:** Normalmente aponta para o **SSM Parameter Store** (Standard Tier).
*   **Integration with RDS:** Se falar em atualizar credenciais no banco automaticamente, a resposta é **Secrets Manager**.
- **Rotate database credentials** → **AWS Secrets Manager**.
- **Configuration storage** → **SSM Parameter Store**.
- **Hierarchical parameters** → **SSM Parameter Store**.
- **API Keys** → Normalmente **Secrets Manager**.
- **Database password rotation** → **Secrets Manager**.
- **Least operational overhead** → **Secrets Manager**.

---

## Regra de Ouro

| Se a questão pedir... | Resposta |
|------------------------|----------|
| Armazenar senhas | **Secrets Manager** |
| Rotacionar senhas automaticamente | **Secrets Manager** |
| Atualizar credenciais do RDS automaticamente | **Secrets Manager** |
| Armazenar parâmetros de configuração | **Parameter Store** |
| Organizar configurações por ambiente | **Parameter Store** |
| Solução mais econômica para configurações | **Parameter Store** |

---

> ⚠️ **Pegadinha de Simulado**
>
> A prova pode tentar te confundir dizendo que o **Parameter Store** é apenas para dados públicos. **Mentira!** Ele pode guardar dados sensíveis usando `SecureString`.
>
> Entretanto, se o enunciado mencionar **rotação automática de credenciais**, **ciclo de vida de senhas**, **integração automática com RDS** ou **troca periódica de segredos**, a resposta correta será **AWS Secrets Manager**.
>
> Outra pegadinha comum é afirmar que o Secrets Manager serve apenas para bancos de dados. Isso é falso. Ele pode armazenar qualquer tipo de segredo, como **API Keys, tokens OAuth, certificados** e **credenciais de aplicações**.

---

* [🏠 Menu Principal](../README.md)
* [⬅️ Criptografia: KMS vs. CloudHSM e a Regra de Ouro](04-criptografia-kms-vs-cloudhsm-golden-rule.md)
* [➡️ Auditória e Logs - Cloudtrail quem fez oque?](06-auditoria-e-logs-cloudtrail-quem-fez-o-que.md)

---
---