# 📓 Caderno de Erros Recorrentes: Estancando o Sangramento de Pontos

Mano, papo reto: o seu maior mestre na preparação para a CLF-C02 não é o instrutor do curso, é o seu próprio erro. Errar no simulado é lucro, porque cada questão perdida revela um ponto cego ou uma pegadinha que a AWS preparou para você. O Caderno de Erros serve para garantir que você não sangre pontos no dia da prova oficial por causa de conceitos que você achou que sabia, mas não dominava 100%.

---

## 1. Por que manter este caderno?

*   **Identificar Padrões de Falha:** Você erra porque não sabe o serviço ou porque lê o enunciado rápido demais?
*   **Mapear Pontos Cegos:** Às vezes você domina S3, mas sempre confunde os planos de suporte. O caderno joga luz no que está escuro.
*   **Revisão Ativa:** Ler o que você mesmo errou e explicou cria uma conexão neural muito mais forte do que apenas ler a documentação oficial.

---

## 2. Template de Registro (Copie e Cole)

Toda vez que errar uma questão nos simulados, preencha este bloco:

### ❌ Registro de Erro: [ID-DA-QUESTÃO]
*   **Enunciado Resumido:** [O que a questão pediu?]
*   **O que eu marquei (Incorreta):** [Sua escolha]
*   **A Resposta Certa:** [Gabarito]
*   **O Motivo Técnico do Erro:** [Onde caí na pegadinha? Esqueci o modelo de responsabilidade? Confundi os limites de tempo?]
*   **Regra de Decisão:** [Para a próxima vez, se eu ler 'X', a resposta deve ser 'Y'.]

---

## 3. Exemplos Práticos de Preenchimento

Aqui estão dois erros clássicos que muita gente comete na trilha de Cloud Practitioner:

### ❌ Registro de Erro: SIMULADO-01-Q09
*   **Enunciado Resumido:** Qual plano de suporte oferece acesso a um Technical Account Manager (TAM) designado?
*   **O que eu marquei (Incorreta):** Business Support.
*   **A Resposta Certa:** Enterprise Support.
*   **O Motivo Técnico do Erro:** Achei que o Business já era "top de linha" o suficiente para ter um gerente. Na real, o Business tem acesso 24/7 a engenheiros, mas o TAM designado (um humano dedicado para a sua conta) é exclusividade do Enterprise.
*   **Regra de Decisão:** Leu "TAM designado" ou "Concierge Support"? A resposta é sempre Enterprise. No Business, o suporte é com um pool de engenheiros, não com uma pessoa específica.

---

### ❌ Registro de Erro: SIMULADO-02-Q18
*   **Enunciado Resumido:** Quem é o responsável por habilitar a criptografia de dados em repouso (at rest) no Amazon S3?
*   **O que eu marquei (Incorreta):** AWS (Provedor).
*   **A Resposta Certa:** Cliente (Usuário).
*   **O Motivo Técnico do Erro:** Confundi a segurança "DA" nuvem com a segurança "NA" nuvem. A AWS fornece a tecnologia (KMS, buckets seguros), mas "apertar o botão" da criptografia é configuração do cliente.
*   **Regra de Decisão:** Criptografia de dados, gerenciamento de chaves e permissões de Bucket são sempre "Security IN the Cloud" (Responsabilidade do Cliente).

---

## 🎯 Gatilho de Exame: Como Revisar

Mano, não deixe para ler o caderno de erros uma vez por mês. A estratégia de guerra é:

1.  **Revisão de Véspera:** No dia anterior à prova, leia apenas o seu caderno de erros e os mnemônicos. Isso vai calibrar o seu "sensor de pegadinhas".

2.  **Foco na Regra de Decisão:** Não decore a resposta da questão (ela não vai cair igual). Decore a sua Regra de Decisão, porque o cenário vai mudar, mas a lógica da AWS é sempre a mesma.

3.  **Triage de Domínios:** Se o seu caderno tem 10 erros de Billing e 2 de Segurança, pare tudo e vá revisar o Módulo de Custos. Os dados não mentem.

> 💡 **Dica de Sênior:** Se você errar a mesma regra de decisão três vezes, você não entendeu o conceito. Volte na documentação ou peça um "debug" da explicação. Não avance com dúvida acumulada!

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Método para Eliminação de Alternativas](02-metodo-de-eliminacao-de-alternativas.md)
* [➡️ Gatilhos Visuais PT-EN](04-gatilhos-visuais-pt-en.md)


---
---