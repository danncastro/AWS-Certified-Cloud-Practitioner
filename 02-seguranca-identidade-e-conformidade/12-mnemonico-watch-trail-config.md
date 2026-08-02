# Monitoramento e Auditoria: Watch vs. Trail vs. Config

Se você não souber a diferença entre esses três serviços, a banca vai te derrubar. Eles parecem falar da mesma coisa (o que está rolando na conta), mas cada um observa um aspecto diferente da infraestrutura. A pegadinha clássica é trocar **quem fez uma ação** (CloudTrail) por **como está a performance** (CloudWatch) ou por **como um recurso estava configurado** (AWS Config).

---

## 1. O Mnemônico Inesquecível

Para não travar na hora da prova, decore estas associações:

* **CloudWATCH = "WATCH the metrics & performance"**

  Pense em um operador olhando para um painel de monitoramento. Ele acompanha CPU, memória, tráfego de rede, latência e erros da aplicação. Seu foco é observar a saúde do ambiente através de **métricas**, **logs** e **alarmes**.

* **CloudTRAIL = "TRAIL of actions"**

  Trail significa "rastro". O CloudTrail registra todas as chamadas de API realizadas na conta AWS, permitindo descobrir **quem fez determinada ação, quando ela aconteceu, de onde veio e qual recurso foi afetado**.

* **AWS CONFIG = "CONFIGuration history & compliance"**

  O AWS Config funciona como uma máquina do tempo da infraestrutura. Ele registra o estado dos recursos ao longo do tempo, mostrando quando uma configuração foi alterada e verificando continuamente se ela continua em conformidade com as regras definidas pela empresa.

---

## 2. Cenário Integrado: A Janela Aberta

Imagine que um desenvolvedor alterou um **Security Group** de uma instância EC2 e liberou a porta SSH (22) para toda a Internet (`0.0.0.0/0`).

Cada serviço responderá uma pergunta diferente:

* **CloudTrail:** registra que o usuário `Dev_Bolado` executou a chamada de API `AuthorizeSecurityGroupIngress` às 14:05, a partir do IP `200.X.X.X`. Ou seja, ele informa **quem realizou a alteração**.

* **AWS Config:** detecta que o Security Group deixou de permitir acesso restrito e passou a aceitar conexões públicas. Caso exista uma Config Rule proibindo SSH aberto, o recurso será marcado como **Non-compliant**. Aqui o foco é mostrar **como a configuração mudou**.

* **CloudWatch:** se essa alteração resultar em aumento de tráfego ou tentativas de invasão, ele poderá identificar o crescimento da métrica **NetworkIn**, disparar um **CloudWatch Alarm** e enviar uma notificação através do **Amazon SNS**. Nesse caso, ele monitora **o impacto operacional** da alteração.

Perceba que os três observaram exatamente o mesmo evento, mas cada um por uma perspectiva diferente.

---

## 3. Tabela de Resolução Rápida

| Recurso | Amazon CloudWatch | AWS CloudTrail | AWS Config |
| :--- | :--- | :--- | :--- |
| **Pergunta Principal** | Como está a performance? | Quem fez a ação? | Como está configurado? |
| **Foco** | Métricas, Logs e Alarmes | Auditoria e Chamadas de API | Configuração e Conformidade |
| **Uso Típico** | CPU alta, erro 500, uso de memória | Descobrir quem alterou ou removeu um recurso | Verificar se um recurso atende às políticas da empresa |
| **Tempo Real** | Alarmes e monitoramento contínuo | Registro contínuo das chamadas de API | Avaliação contínua das configurações |
| **Escopo** | Regional | Global (eventos IAM) e Regional (demais serviços) | Regional |

---

## 4. Quando usar cada um?

Sempre tente responder mentalmente à pergunta do enunciado.

| Se a questão perguntar... | Serviço |
|---------------------------|----------|
| Como está a CPU da EC2? | Amazon CloudWatch |
| Quem apagou uma instância? | AWS CloudTrail |
| Quem alterou um Security Group? | AWS CloudTrail |
| Meu bucket S3 está público? | AWS Config |
| Quero receber alerta quando a CPU passar de 80%. | Amazon CloudWatch |
| Quero saber quando um recurso ficou fora de conformidade. | AWS Config |

---

## 🎯 Gatilho de Exame

Se aparecer estes termos no enunciado, normalmente a resposta será:

### Amazon CloudWatch

- Performance metrics
- CPU utilization
- Memory monitoring
- Application logs
- CloudWatch Logs
- CloudWatch Alarms
- NetworkIn / NetworkOut

### AWS CloudTrail

- API call history
- Audit logs
- User activity
- Governance
- Management events
- Who performed an action

### AWS Config

- Configuration history
- Resource configuration
- Compliance
- Config Rules
- Drift detection
- Continuous evaluation

---

## Pegadinhas da Prova

| Se a questão perguntar... | Resposta |
|---------------------------|----------|
| CPU, memória, latência ou métricas | CloudWatch |
| Quem criou ou apagou um recurso | CloudTrail |
| Histórico de configuração de um recurso | AWS Config |
| Recurso está em conformidade? | AWS Config |
| Logs de auditoria de chamadas de API | CloudTrail |
| Alarmes quando CPU passar de determinado valor | CloudWatch |

---

> **💡 Dica de Ouro:** Faça sempre esta associação mental:
>
> - **CloudWatch → Performance**
> - **CloudTrail → Auditoria**
> - **AWS Config → Configuração e Conformidade**
>
> Se decorar apenas essa tríade, você resolve a maioria das questões da CLF-C02 sobre monitoramento.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 2: Síntese IAM: User vs. Group vs. Role](11-tabela-iam-user-vs-group-vs-role.md)
* [➡️ Módulo 2: Lab: Configurando Políticas IAM e MFA](13-lab-configurando-politicas-iam-e-mfa.md)

---
---