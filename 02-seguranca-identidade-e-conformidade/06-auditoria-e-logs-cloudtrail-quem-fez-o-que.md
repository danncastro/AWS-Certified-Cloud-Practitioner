# Auditoria e Logs: AWS CloudTrail (Quem fez o quê?)

Em um ambiente de produção, nunca deveria existir a resposta:

> "Não sei quem apagou essa instância."

Na AWS, praticamente toda ação realizada no console, na CLI, em um SDK ou por outro serviço gera uma **chamada de API**. O **AWS CloudTrail** é o serviço responsável por registrar essas chamadas, fornecendo rastreabilidade, auditoria e conformidade.

Pense nele como a **"caixa-preta"** da sua conta AWS.

---

## 1. A Pergunta de Ouro do CloudTrail

O CloudTrail não está preocupado se o seu site está lento (isso é tarefa do CloudWatch). O foco dele é a **rastreabilidade**. Ele responde às perguntas críticas que o seu time de segurança e compliance vai te fazer:

*   **Quem** realizou a ação? (Qual usuário IAM ou Role?)
*   **Qual** API foi chamada? (Ex: `TerminateInstances`, `DeleteBucket`)
*   **Qual** recurso foi afetado? (Qual instância específica ou bucket?)
*   **Quando** aconteceu? (Data e hora exata)
*   **De onde** veio a requisição? (Endereço IP de origem)

---

### Como o CloudTrail funciona?

Sempre que uma ação acontece na conta AWS, um evento é gerado.

~~~mermaid
flowchart LR

User["Usuário / CLI / SDK"]

API["AWS API"]

CT["AWS CloudTrail"]

S3["Amazon S3"]

CW["CloudWatch Logs"]

User --> API

API --> CT

CT --> S3

CT --> CW
~~~

Esses eventos podem ser consultados diretamente no console ou armazenados para auditorias futuras.

---

## 2. Conceitos-Chave: Do Histórico à Persistência

Para a prova CLF-C02, você precisa entender como o serviço se organiza para não queimar dinheiro e nem perder dados:

*   **Event History (Histórico de Eventos):** Por padrão, o CloudTrail já vem ativado e guarda os últimos **90 dias** de eventos de gerenciamento gratuitamente. É o que você vê direto no console para um troubleshooting rápido.
*   **Trails (Trilhas):** Se você precisa guardar os logs por anos (para compliance) ou analisar em massa, você cria um **Trail**. Isso permite gravar e persistir os logs de forma contínua em um bucket do **Amazon S3** ou enviá-los para o **CloudWatch Logs**.
*   **CloudTrail Insights:** É a inteligência do serviço. Ele analisa o seu padrão normal de chamadas de API e gera um alerta automático se detectar algo bizarro, como um pico anormal de criação de instâncias ou milhares de tentativas de login falhas vindas de um IP estranho.

---

### Tipos de Eventos

O CloudTrail pode registrar diferentes categorias de eventos.

---

#### Management Events

São os eventos administrativos.

Exemplos:

- criação de usuários IAM;
- criação de EC2;
- alteração de Security Groups;
- criação de Buckets S3;
- alteração de Roles.

Esses são os eventos registrados no **Event History**.

---

#### Data Events

Registram operações realizadas **dentro dos recursos**.

Exemplos:

- leitura de objetos no S3;
- upload de arquivos;
- execução de funções Lambda.

Esses eventos **não são registrados por padrão**, pois podem gerar grande volume de logs.

---

#### Insights Events

Eventos gerados pelo próprio CloudTrail quando ele identifica comportamento fora do padrão.

---

## 3. CloudTrail vs. CloudWatch: Não confunda as bolas!

Essa é a pegadinha favorita da banca. Memorize a diferença de propósito para não cair na vala comum:

*   **AWS CloudTrail:** Focado em **Auditoria e Ações**. Ele responde: **"Quem fez o quê?"** (*Who did what?*). É o histórico das chamadas de API feitas por usuários ou serviços.
*   **Amazon CloudWatch:** Focado em **Performance e Saúde**. Ele responde: **"Como está o desempenho do sistema?"** (*How is the system performing?*). Ele cuida de métricas de CPU, alarmes de custo e logs de dentro do sistema operacional ou da aplicação.

---

> **Sinal de Alerta:** Se o enunciado fala em "investigar quem deletou um recurso", a resposta é sempre **CloudTrail**. Se fala em "monitorar o uso de CPU ou memória de uma instância", a resposta é **CloudWatch**.

---

#### CloudTrail responde:

- Quem criou uma instância?
- Quem apagou um Bucket?
- Quem alterou uma Policy?
- Quem fez login?

---

#### CloudWatch responde:

- CPU está alta?
- Memória está cheia?*
- Houve aumento de latência?
- O Auto Scaling deve iniciar novas instâncias?

> **\*** A métrica de memória não é enviada automaticamente pelas instâncias EC2; normalmente é necessário instalar o **CloudWatch Agent**.

---

## 4. Casos de Uso

Utilize o CloudTrail quando precisar:

- descobrir quem realizou uma ação;
- atender requisitos de auditoria;
- investigar incidentes de segurança;
- manter conformidade (Compliance);
- registrar todas as chamadas de API da conta.

---

### Regra de Ouro

| Pergunta | Serviço |
|----------|----------|
| Quem apagou a EC2? | **CloudTrail** |
| Quem alterou uma IAM Policy? | **CloudTrail** |
| Quem criou um Bucket? | **CloudTrail** |
| CPU acima de 90%? | **CloudWatch** |
| Criar um alarme para utilização de CPU | **CloudWatch** |
| Receber alerta quando a CPU aumentar | **CloudWatch** |


---

## 🎯 Gatilho de Exame

Se você ler estes termos em inglês no enunciado, o foco da questão é o CloudTrail:

*   **AWS CloudTrail:** Serviço de auditoria, governança e conformidade.
*   **API call history:** O registro de tudo o que foi solicitado via console, CLI ou SDK.
*   **Governance and compliance:** O objetivo principal de negócio do serviço.
*   **User activity tracking:** Rastrear o que as identidades estão fazendo na conta.
*   **CloudTrail Insights:** Recurso para detecção de anomalias e comportamentos incomuns.
*   **Audit logs:** Sinônimo para o histórico gerado pelo serviço.
*   **CloudTrail vs CloudWatch:** Trilha de API vs. Monitoramento de performance.
- **Trail:** Armazenamento contínuo de eventos.
- **Event History:** Últimos 90 dias de eventos de gerenciamento.

---

### CloudTrail x CloudWatch em uma frase

- **CloudTrail:** registra **ações**.
- **CloudWatch:** monitora **comportamento**.

Ou, de forma ainda mais simples:

- **CloudTrail:** **Quem fez?**
- **CloudWatch:** **Como está?**

Essa associação resolve boa parte das questões da certificação.

---

> ⚠️ **Dica de Sênior**
>
> O CloudTrail registra **chamadas de API realizadas na conta AWS**, mas **não monitora o desempenho da infraestrutura**.
>
> Se a questão perguntar:
>
> - **"Quem excluiu um recurso?"** → **CloudTrail**
> - **"CPU elevada?"** → **CloudWatch**
> - **"Criar alarmes de utilização?"** → **CloudWatch**
> - **"Registrar todas as ações realizadas pelos usuários?"** → **CloudTrail**
>
> Outra pegadinha comum é afirmar que o CloudTrail registra apenas ações feitas pelo Console. Isso é falso. Ele registra chamadas realizadas pelo **AWS Management Console, AWS CLI, SDKs e diversos serviços da própria AWS**.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 2: Gestão de Segredos: Secrets Manager vs. Parameter Store](05-gestao-de-segredos-secrets-manager-vs-parameter-store.md)
* [➡️ Módulo 2: Detecção de Ameaças: GuardDuty (ML) vs. Inspector (Vulnerabilidades)](07-deteccao-de-ameacas-guardduty-ml-vs-inspector-vuln.md)

---
---