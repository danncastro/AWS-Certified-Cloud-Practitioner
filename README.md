# AWS Certified Cloud Practitioner (CLF-C02) - Trilha de Aceleração

![AWS Certified](https://img.shields.io/badge/AWS-Certified-orange?style=for-the-badge&logo=amazon-aws)
![Exam](https://img.shields.io/badge/Exam-CLF--C02-blue?style=for-the-badge)
![Nivel](https://img.shields.io/badge/Nível-Iniciante/Intermediário-blue?style=for-the-badge)

Este repositório centraliza a documentação técnica, laboratórios práticos e simulados focados na preparação para o exame **AWS Certified Cloud Practitioner (CLF-C02)**. 

O objetivo é cobrir de forma objetiva todo o blueprint oficial da certificação, incluindo os tópicos recentes de IA Generativa (Amazon Bedrock e Amazon Q), arquitetura resiliente, segurança e governança de custos. O material é estruturado para engenharia, com foco em entender o comportamento dos serviços AWS, mitigar pegadinhas de tradução da banca examinadora e consolidar a base necessária para operação no console e CLI.

---

## 📌 Sumário

1. [Contexto Real da Prova](#-contexto-real-da-prova)
2. [Como Usar este Material](#%EF%B8%8F-como-usar-este-material)
3. [Estrutura do Repositório](#-estrutura-do-repositório)
4. [Metodologia de Estudo Sugerida](#-metodologia-de-estudo-sugerida)
5. [Créditos e Parceria](#-créditos-e-parceria)

---

## 🎯 Contexto Real da Prova

A prova Cloud Practitioner evoluiu. Esqueça o teste de vocabulário simples; o exame agora exige que você saiba julgar cenários arquiteturais. Os pilares que definem o sucesso hoje são:

*   **IA Generativa:** O escopo agora exige conhecimento sobre Amazon Bedrock, Amazon Q, LLMs e o impacto de modelos fundacionais no negócio.
*   **FinOps e Gestão de Custos:** Você precisa dominar a diferença entre CapEx e OpEx, calcular o TCO (*Total Cost of Ownership*) e saber configure alertas proativos com o AWS Budgets.
*   **Modelo de Responsabilidade Compartilhada:** É mandatório saber onde termina o trabalho da AWS (segurança **da** nuvem) e onde começa o seu (segurança **na** nuvem), distinguindo as camadas de IaaS, PaaS e SaaS.

---

## 🛠️ Como usar este Material

Este guia foi modularizado em **micro-arquivos** focados em engenharia. A dinâmica de leitura é baseada em consumo rápido e fixação:

- **Tabelas Comparativas:** Use-as para matar as questões de "pegadinha" e limiar de decisão (Ex: SG vs NACL, S3 vs EBS vs EFS).
- **Cenários de Uso:** Em vez de decorar o que o serviço faz, entenda o problema arquitetural que ele resolve.
- **Labs Práticos:** Passo a passo simplificado focado em console e conceitos reais.
- **Estratégia Dual-Language (PT-EN):** Embora a documentação esteja em português, a banca da AWS peca frequentemente na tradução das questões. Por isso, todos os arquivos possuem uma seção de **🎯 Gatilho de Exame** mapeando os termos técnicos originais em inglês (*"Pay-as-you-go"*, *"Undifferentiated heavy lifting"*, etc.). Use esses gatilhos para identificar a resposta correta instantaneamente, mesmo se a tradução estiver confusa.

---

# 🗺️ Navegação Rápida por Módulos

Clique em qualquer um dos módulos abaixo para ir direto ao README.md correspondente no repositório:

| Módulo | Descrição do Conteúdo | Atalho Direto |
| :--- | :--- | :---: |
| 🪖 **00. Estratégias de Guerra** | Panorama do exame, técnicas de leitura e caderno de erros. | [Acessar 📄](./00-estrategias-de-guerra/README.md) |
| 🌐 **01. Fundamentos & Infra Global** | Cloud computing, Regiões, AZs, Shared Responsibility e CaPex/OpEx. | [Acessar 📄](./01-fundamentos-e-infraestrutura-global/README.md) |
| 🔐 **02. Segurança & Conformidade** | IAM, MFA, Shield/WAF, KMS, Secrets Manager, CloudTrail e GuardDuty. | [Acessar 📄](./02-seguranca-identidade-e-conformidade/README.md) |
| 💻 **03. Computação & Containers** | EC2, Auto Scaling, ELB, Lambda, ECS, Fargate e EKS. | [Acessar 📄](./03-computacao-e-containers/README.md) |
| 📦 **04. Armazenamento & Migração** | S3 (classes e ciclo de vida), EBS, EFS, Glacier e Família Snow. | [Acessar 📄](./04-armazenamento-e-transferencia/README.md) |
| 🗄️ **05. Bancos de Dados & Analytics** | RDS, Aurora, DynamoDB, Redshift, Athena e ElastiCache. | [Acessar 📄](./05-bancos-de-dados-e-analytics/README.md) |
| 🔌 **06. Redes & Conectividade** | VPC, Subnets, IGW/NAT, SG vs NACL, Route 53 e Transit Gateway. | [Acessar 📄](./06-redes-e-conectividade/README.md) |
| 🤖 **07. IA Generativa & Inovação** | LLMs, Amazon Bedrock, Amazon Q, SageMaker e serviços de IA práticos. | [Acessar 📄](./07-inteligencia-artificial-e-inovacao/README.md) |
| 🏗️ **08. Arquitetura & AWS CAF** | Well-Architected Framework (6 pilares), CAF e as estratégias dos 7 Rs. | [Acessar 📄](./08-arquitetura-e-adocao-aws-caf/README.md) |
| 💰 **09. Gestão de Custos & Governança** | AWS Organizations, Control Tower, SCPs, Cost Explorer e Planos de Suporte. | [Acessar 📄](./09-gestao-de-custos-e-governanca/README.md) |
| 🚀 **10. Preparação Final** | Cronograma de 30 dias, Checklist, Glossário PT-EN e Simulados Completos. | [Acessar 📄](./10-preparacao-final/README.md) |

---

## 📈 Metodologia de Estudo Sugerida

Não tente comer o elefante de uma vez só. Siga este fluxo para não surtar:

1.  **Leitura Atômica (25 min):** Foque em um micro-arquivo por vez. Não tente engolir o módulo inteiro de uma paulada. Leia o arquivo do módulo. Se o texto falar de "Dica de Prova", pare e anote.
2.  **Mapeamento de Gatilhos:** Identifique os termos técnicos em inglês dentro do texto e associe ao problema que eles resolvem (ex: *"Auditoria"* ➔ CloudTrail).
3.  **Mão na Massa (Labs):** Siga os guias práticos para subir a infraestrutura. O que o olho vê e a mão faz, o cérebro não esquece. Vá para o arquivo de Lab do módulo. Abra sua conta AWS (Free Tier!) e faça. Ver o serviço funcionando vale mais que 10 leituras.
4.  **Micro-simulado de Retenção:** Resolva o simulado ao final de cada módulo. Se acertar menos de 70%, volte na teoria.
5.  **O Segredo (Caderno de Erros):** Errou uma questão? Não olhe só a resposta certa. Vá no xx-caderno-de-erros.md e anote por que você caiu na pegadinha. Registre o motivo técnico e a regra de decisão para não repetir o padrão. Isso é o que te aprova.

---

## 🤝 Créditos e Parceria

Este projeto é o resultado da colaboração de alto nível entre a capacidade analítica e de síntese de IA e a visão estratégica de engenharia do usuário.

Este repositório não é um "copia e cola" da internet. Ele é o resultado de uma engenharia pesada de cruzamento de fontes reais.

- **Idealização e Estrutura:** Mente do estudante focada em eficiência e resultados.
- **Processamento e Redação:** Poder de análise do **NotebookLM** integrado ao **Gemini**, via prompts avançados para garantir densidade técnica com leitura fluida.
- **Filosofia:** *Cloud is for everyone, but mastery is for those who practice.*

**Bora pra cima dessa certificação! 🚀**

---
---