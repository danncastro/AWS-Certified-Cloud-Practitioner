# ✂️ Método de Eliminacão de Alternativas: Vencendo por Exclusão

Manos, na prova CLF-C02, muitas vezes você não precisa saber a resposta certa de cara, mas sim saber identificar por que as outras três estão erradas. A banca da AWS adora colocar distratores que parecem profissionais, mas que violam princípios básicos de arquitetura ou simplesmente não existem. Vamos aprender a limpar o terreno.

---

## 1. A Filosofia Well-Architected: O "Filtro do Absurdo"

A AWS nunca dará como correta uma alternativa que fira as boas práticas do *Well-Architected Framework* ou do *Modelo de Responsabilidade Compartilhada*. Se a opção sugere algo que aumente o risco ou a carga operacional sem motivo, elimine-a imediatamente.

*   **Uso de Conta Root:** Se a alternativa diz para usar a conta Root para tarefas diárias ou automação, está errada. O correto é sempre usar usuários ou roles do IAM.
*   **Chaves Fixas (*Hardcoded*):** Opções que sugerem salvar *Access Keys* dentro do código da aplicação ou em arquivos de texto no EC2 são descartes automáticos. A resposta certa envolverá obrigatoriamente *IAM Roles*.
*   **Permissões Amplas:** Alternativas que sugerem liberar `0.0.0.0/0` (acesso total) para portas sensíveis como SSH (22) ou RDP (3389) por "conveniência" estão incorretas. A AWS exige o Princípio do Menor Privilégio (*Least Privilege*).
*   **Segurança Física:** Se a alternativa diz que você (cliente) deve configurar a segurança das câmeras do data center ou trocar discos rígidos defeituosos, descarte. Isso é responsabilidade **DA** nuvem (exclusiva da AWS).

---

## 2. O Padrão das "Falsas Gêmeas"

A banca coloca serviços com nomes ou siglas parecidas para confundir quem estudou apenas por cima. Aprenda o limiar de diferença para eliminar a opção errada:

| Serviço A | Serviço B | Como diferenciar para eliminar |
| :--- | :--- | :--- |
| **AWS CloudTrail** | **Amazon CloudWatch** | **Trail** é auditoria (quem fez o quê via API). **Watch** é monitoramento (performance, métricas e logs). |
| **AWS Inspector** | **AWS Artifact** | **Inspector** escaneia vulnerabilidades no EC2/ECR. **Artifact** é o portal para baixar relatórios de conformidade (ISO, PCI, SOC). |
| **Security Groups** | **NACL** | **SG** é no nível da instância e mantém estado (*stateful*). **NACL** é no nível da subnet e não mantém estado (*stateless*). |
| **AWS KMS** | **AWS CloudHSM** | **KMS** é multilocatário e gerenciado pela AWS. **CloudHSM** é hardware dedicado onde você tem controle total das chaves. |
| **AWS Secrets Manager** | **AWS Systems Manager Parameter Store** | **Secrets Manager** foca em segredos sensíveis com rotação automática de senhas. **Parameter Store** é para configurações gerais e strings simples. |

---

## 3. Serviços Fantasmas e Inventados

Para completar as 4 alternativas (A, B, C, D), a banca frequentemente inventa nomes que "soam como AWS", mas não existem no ecossistema real. Se você nunca viu o nome no material oficial, há 99% de chance de ser um Serviço Fantasma.

*   **Exemplos de Fakes da Banca:** *AWS Global Storage*, *Amazon DNS Guard*, *AWS Auto-Security*, *Amazon Cloud Firewall*.

>   **💡 Dica de Ouro:** Se o nome do serviço parece descrever perfeitamente o que a questão pede de forma genérica demais, desconfie. A AWS costuma usar nomes comerciais próprios (Ex: **Amazon GuardDuty** em vez de *AWS Intrusion Detector*).

---

## 4. Matriz de Decisão Rápida por Exclusão

Use esta tabela mental para matar alternativas que batem de frente com o requisito principal do enunciado:

| Se o requisito core é... | Elimine imediatamente opções que falem em... |
| :--- | :--- |
| **Menor Custo (*Cost-effective*)** | Instâncias *On-Demand*, *Provisioned IOPS*, arquiteturas *Multi-Region*. |
| **Menor Esforço Operacional** | Instalar software manual no EC2, scripts crons, gerenciar patches de S.O. |
| **Alta Disponibilidade** | Arquiteturas *Single-AZ*, instâncias únicas sem backup, processos manuais. |
| **Conexão Dedicada/Privada** | Internet pública, conexões baseadas apenas em browser, VPN (se o foco for latência fixa). |
| **Escala Imediata (Picos)** | Redimensionamento manual de instâncias, capacidade fixa e engessada. |

---

## 🎯 Gatilho de Exame: O Fluxo de Descarte

Para cada alternativa na hora da prova, faça o seguinte *check* mental rápido:

1. **Isso existe?** (Se o nome do serviço é inventado ou genérico, elimine).

2. **Isso é seguro?** (Se pede Root, credenciais fixas ou exposição pública, elimine).

3. **Isso é gerenciado?** (Se pede para você fazer trabalho manual de infra e o enunciado exige agilidade, elimine).

4. **Isso resolve o problema real?** (Às vezes a alternativa traz uma excelente prática da AWS, mas não responde o que o comando final perguntou).

> ⚖️ **A Regra de Ouro:** Se restarem duas opções que parecem certas após a limpa, a alternativa que trouxer o serviço mais gerenciado (*SaaS/Serverless*) ou que estiver perfeitamente alinhada com a palavra de comando principal (Ex: custo vs performance) será a vencedora.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Tecnicas de Leitura de Questões](01-tecnicas-de-leitura-de-questoes.md)
* [➡️ Caderno de Erros Recorrentes](03-caderno-de-erros-recorrentes.md)

---
---