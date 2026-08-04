# Checklist Final: Prontidão e Aprovação (DoD)

Se você chegou até aqui, já percorreu todo o caminho. Passou pelos conceitos, conheceu os principais serviços, fez laboratórios, revisou os módulos e encarou simulados.

Agora o objetivo não é aprender conteúdo novo.

O objetivo é **evitar erros bobos** no dia da prova.

Este capítulo funciona como uma inspeção final antes da decolagem. Revise cada item com calma e só marque como concluído quando realmente estiver seguro.

---

# 1. Validação Técnica (Checklist por Domínio)

Antes da prova, confirme que você consegue responder às perguntas abaixo **sem consultar o material**.

Se algum item gerar dúvida, volte naquele módulo e revise apenas aquele assunto.

## ☁️ Domínio 1 — Cloud Concepts (24%)

- [ ] Consigo explicar a diferença entre **Elasticidade** e **Escalabilidade**?
- [ ] Sei por que a computação em nuvem reduz investimentos iniciais (CapEx → OpEx)?
- [ ] Entendo o conceito de **Economia de Escala** da AWS?
- [ ] Sei diferenciar Alta Disponibilidade, Tolerância a Falhas e Recuperação de Desastres?

> **Dica:** Esse domínio cobra muito mais entendimento de conceitos do que nomes de serviços.

---

## 🔐 Domínio 2 — Segurança e Conformidade (30%)

- [ ] Sei explicar o **Modelo de Responsabilidade Compartilhada**?
- [ ] Entendo quando utilizar **IAM User**, **Group** e **Role**?
- [ ] Sei por que aplicações devem usar **Roles**, e não usuários IAM?
- [ ] Diferencio rapidamente:
  - CloudTrail × CloudWatch
  - GuardDuty × Inspector
  - Shield × WAF
- [ ] Sei para que servem MFA, KMS e Secrets Manager?

> **Essa é uma das áreas favoritas da prova.** Se Segurança ainda gera dúvidas, vale a pena dedicar uma última revisão.

---

## 🖥️ Domínio 3 — Tecnologia e Serviços (34%)

- [ ] Consigo escolher entre **S3, EBS e EFS** em poucos segundos?
- [ ] Sei quando usar **EC2**, **Lambda**, **ECS**, **EKS** e **Fargate**?
- [ ] Diferencio bancos relacionais (**RDS**) de NoSQL (**DynamoDB**)?
- [ ] Entendo o papel do **CloudFront** e das **Edge Locations**?
- [ ] Sei diferenciar **Security Group** de **Network ACL**?

> Se você consegue eliminar rapidamente os serviços errados, já está pensando como a banca.

---

## 💰 Domínio 4 — Billing, Pricing e Support (12%)

- [ ] Sei diferenciar:
  - AWS Budgets
  - Cost Explorer
  - Pricing Calculator
  - Cost Anomaly Detection
- [ ] Conheço os planos de suporte da AWS?
- [ ] Sei qual plano oferece um **Technical Account Manager (TAM)**?

Embora seja o domínio com menor peso, ele costuma render pontos fáceis.

---

# 2. Logística da Prova

Muita gente perde concentração por problemas que poderiam ter sido evitados.

Resolva tudo isso **antes** do dia da prova.

---

## 💻 Se for fazer Online

Confira:

- [ ] Mesa completamente limpa.
- [ ] Apenas um monitor conectado.
- [ ] Celular desligado e fora do alcance.
- [ ] Ambiente silencioso.
- [ ] Documento original separado.
- [ ] Webcam funcionando corretamente.
- [ ] Microfone funcionando.
- [ ] Internet estável (preferencialmente via cabo).
- [ ] Teste do sistema realizado previamente no mesmo computador.

> Não deixe para descobrir problemas técnicos minutos antes da prova.

---

## 🏢 Se for fazer no Centro de Testes

Confira:

- [ ] Chegar pelo menos 30 minutos antes.
- [ ] Documento(s) exigido(s) separado(s).
- [ ] Confirmar o endereço do local.
- [ ] Planejar estacionamento ou transporte.

Quanto menos preocupação logística, mais foco sobra para resolver as questões.

---

# 3. Estratégia Durante a Prova

A CLF-C02 possui **65 questões para 90 minutos**.

Na prática, isso significa aproximadamente **1 minuto e 20 segundos por questão**.

Não é uma prova corrida.

Ela é uma prova de atenção.

---

## Leia procurando palavras-chave

A AWS adora esconder a resposta em uma única expressão.

Fique atento principalmente a termos como:

- **BEST**
- **MOST**
- **LOWEST COST**
- **LEAST OPERATIONAL EFFORT**
- **HIGHLY AVAILABLE**
- **SERVERLESS**
- **MANAGED**
- **SECURE**
- **COMPLIANT**

Essas palavras normalmente eliminam metade das alternativas.

---

## Utilize o Método das 3 Passadas

### Primeira passada

Resolva apenas as questões que você sabe imediatamente.

Se ficou em dúvida, marque para revisão e siga.

---

### Segunda passada

Volte nas questões marcadas.

Agora:

- elimine alternativas claramente incorretas;
- compare apenas as opções restantes;
- procure a palavra-chave do cenário.

---

### Terceira passada

Faça uma revisão rápida.

Só altere uma resposta se perceber que:

- leu errado;
- confundiu um serviço;
- encontrou uma informação objetiva que passou despercebida.

Trocar resposta "porque bateu insegurança" costuma diminuir a nota.

---

## Nunca deixe questão em branco

Não existe penalidade por erro.

Se não souber, elimine o máximo possível e escolha a alternativa mais provável.

Uma resposta errada ainda vale mais do que uma resposta em branco.

---

# 4. Definition of Done (DoD)

Considere este guia concluído apenas quando todos os itens abaixo estiverem marcados.

- [ ] **DoD-01:** Fiz pelo menos **dois simulados completos** (65 questões).
- [ ] **DoD-02:** Obtive aproximadamente **85% de acertos** ou mais nos simulados.
- [ ] **DoD-03:** Consigo explicar o Modelo de Responsabilidade Compartilhada sem consultar material.
- [ ] **DoD-04:** Sei identificar rapidamente os seis pilares do Well-Architected Framework.
- [ ] **DoD-05:** Diferencio os principais serviços que costumam aparecer como pegadinhas.
- [ ] **DoD-06:** Consigo reconhecer quando a resposta deve ser um serviço Gerenciado ou Serverless.
- [ ] **DoD-07:** Sei interpretar palavras-chave como **BEST**, **MOST**, **LOWEST COST** e **LEAST OPERATIONAL EFFORT**.
- [ ] **DoD-08:** Estou descansado e confiante para realizar a prova.

Se todos os itens estiverem marcados, você provavelmente já está pronto.

---

# 🎯 Gatilho de Exame

Na reta final, pare de decorar definições e comece a reconhecer padrões.

Quando ler...

- **Menor esforço operacional** → Serviço Gerenciado ou Serverless.
- **Executar código por evento** → AWS Lambda.
- **Compartilhar arquivos entre várias instâncias Linux** → Amazon EFS.
- **Armazenar arquivos** → Amazon S3.
- **Disco para uma instância EC2** → Amazon EBS.
- **Auditoria de chamadas de API** → AWS CloudTrail.
- **Monitoramento e métricas** → Amazon CloudWatch.
- **Alerta de orçamento** → AWS Budgets.
- **Analisar gastos** → Cost Explorer.
- **Baixa latência global** → Amazon CloudFront.
- **Privilégio mínimo** → IAM.
- **Alta disponibilidade dentro da mesma região** → Múltiplas Availability Zones.

> **Grande pegadinha da CLF-C02:** frequentemente mais de uma alternativa funciona. A resposta correta será aquela que atende ao requisito com **menor custo**, **menor esforço operacional** ou utilizando um **serviço gerenciado**, quando o cenário permitir.

---

> ## ✅ Missão Cumprida

Mano, papo reto...

Se você chegou até aqui, não começou ontem.

Você já construiu uma base sólida, revisou os conceitos importantes e enfrentou simulados suficientes para entender o estilo da prova.

Agora é confiar no processo.

Leia cada questão com calma.

Procure as palavras-chave.

Elimine as alternativas improváveis.

E lembre-se: a AWS não quer saber se você decorou documentação. Ela quer validar se você consegue identificar a solução mais adequada para um cenário de negócio.

Respira fundo, administra o tempo e segue firme.

**Boa prova!** e **Marcha! 🚀**


---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 10: Simulado Completo CLF-C02: Versão 2 - O Teste Final](03-simulado-completo-v2-blueprint-real.md)

---