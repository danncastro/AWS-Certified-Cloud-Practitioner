# Micro-Simulado: Segurança, Identidade e Conformidade

O domínio de **Segurança** é um dos mais importantes da prova CLF-C02. A AWS espera que você saiba identificar o serviço correto para cada cenário, principalmente quando as alternativas parecem muito parecidas.

Bora validar se esses conceitos já estão na ponta da língua.

---

## Questões

### 1. Uma aplicação executando em uma instância Amazon EC2 precisa acessar objetos armazenados em um bucket Amazon S3. Seguindo as melhores práticas de segurança, qual abordagem deve ser utilizada?

A) Criar um **IAM User** e armazenar as **Access Keys** no código da aplicação.

B) Anexar uma **IAM Role** com as permissões necessárias à instância EC2.

C) Tornar o bucket público por meio da **Bucket Policy**.

D) Executar a aplicação utilizando a conta **Root** da AWS.

<details>
<summary><strong>💡 Gabarito Comentado</strong></summary>

**✅ Correta:** **B.** A **IAM Role** fornece credenciais temporárias para a instância EC2, eliminando o uso de chaves fixas e seguindo o princípio do menor privilégio.

**❌ Incorreta A:** Nunca armazene Access Keys no código da aplicação.

**❌ Incorreta C:** Tornar o bucket público expõe os dados desnecessariamente.

**❌ Incorreta D:** A conta Root nunca deve ser utilizada por aplicações.

</details>

---

### 2. Um arquiteto precisa proteger uma aplicação web contra ataques DDoS e deseja contar com suporte especializado durante ataques ativos. Qual serviço atende esse requisito?

A) AWS WAF.

B) AWS Shield Standard.

C) AWS Shield Advanced.

D) Amazon GuardDuty.

<details>
<summary><strong>💡 Gabarito Comentado</strong></summary>

**✅ Correta:** **C.** O **AWS Shield Advanced** oferece proteção avançada contra ataques DDoS e acesso ao **DDoS Response Team (DRT)**.

**❌ Incorreta A:** O WAF protege aplicações web (Camada 7), mas não substitui o Shield contra ataques DDoS volumétricos.

**❌ Incorreta B:** O Shield Standard fornece proteção básica, porém não inclui o DRT.

**❌ Incorreta D:** O GuardDuty detecta ameaças, mas não mitiga ataques DDoS.

</details>

---

### 3. Após um incidente de segurança, a equipe precisa descobrir quem excluiu uma instância EC2, quando isso ocorreu e de qual endereço IP partiu a requisição. Qual serviço fornece esse histórico?

A) Amazon CloudWatch.

B) AWS CloudTrail.

C) AWS Config.

D) Amazon Inspector.

<details>
<summary><strong>💡 Gabarito Comentado</strong></summary>

**✅ Correta:** **B.** O **AWS CloudTrail** registra todas as chamadas de API, incluindo usuário, horário, endereço IP e ação executada.

**❌ Incorreta A:** O CloudWatch monitora métricas e logs, não auditoria de APIs.

**❌ Incorreta C:** O AWS Config registra alterações na configuração dos recursos.

**❌ Incorreta D:** O Inspector identifica vulnerabilidades.

</details>

---

### 4. Uma startup deseja identificar automaticamente vulnerabilidades de software e portas abertas em instâncias EC2 e imagens armazenadas no Amazon ECR. Qual serviço realiza esse trabalho?

A) Amazon GuardDuty.

B) Amazon Inspector.

C) AWS WAF.

D) Amazon Macie.

<details>
<summary><strong>💡 Gabarito Comentado</strong></summary>

**✅ Correta:** **B.** O **Amazon Inspector** realiza avaliações automáticas de vulnerabilidades e exposição de rede em EC2 e imagens do ECR.

**❌ Incorreta A:** O GuardDuty detecta atividades suspeitas, não vulnerabilidades de software.

**❌ Incorreta C:** O WAF protege aplicações web.

**❌ Incorreta D:** O Macie identifica dados sensíveis no Amazon S3.

</details>

---

### 5. Um banco digital deseja identificar automaticamente informações sensíveis (PII), como CPF e números de cartão de crédito, armazenadas em buckets Amazon S3. Qual serviço deve ser utilizado?

A) Amazon Macie.

B) Amazon GuardDuty.

C) AWS KMS.

D) AWS Artifact.

<details>
<summary><strong>💡 Gabarito Comentado</strong></summary>

**✅ Correta:** **A.** O **Amazon Macie** utiliza Machine Learning para descobrir, classificar e proteger dados sensíveis armazenados no Amazon S3.

**❌ Incorreta B:** O GuardDuty monitora ameaças e comportamentos suspeitos.

**❌ Incorreta C:** O KMS gerencia chaves de criptografia, mas não identifica PII.

**❌ Incorreta D:** O Artifact fornece documentos de conformidade.

</details>

---

### 6. Um auditor solicitou os relatórios SOC e ISO da infraestrutura da AWS para validar requisitos de conformidade. Onde esses documentos podem ser obtidos?

A) AWS CloudTrail.

B) AWS Trusted Advisor.

C) AWS Artifact.

D) AWS Secrets Manager.

<details>
<summary><strong>💡 Gabarito Comentado</strong></summary>

**✅ Correta:** **C.** O **AWS Artifact** disponibiliza relatórios de auditoria, certificações e acordos de conformidade.

**❌ Incorreta A:** O CloudTrail registra eventos de API.

**❌ Incorreta B:** O Trusted Advisor fornece recomendações de boas práticas.

**❌ Incorreta D:** O Secrets Manager armazena segredos.

</details>

---

### 7. Uma empresa deseja rotacionar automaticamente a senha de um banco Amazon RDS a cada 30 dias, sem intervenção manual. Qual serviço oferece esse recurso?

A) AWS Systems Manager Parameter Store.

B) AWS Secrets Manager.

C) AWS KMS.

D) Amazon CloudWatch.

<details>
<summary><strong>💡 Gabarito Comentado</strong></summary>

**✅ Correta:** **B.** O **AWS Secrets Manager** oferece rotação automática de segredos e integração nativa com o Amazon RDS.

**❌ Incorreta A:** O Parameter Store armazena parâmetros e segredos, mas não possui rotação automática nativa.

**❌ Incorreta C:** O KMS gerencia chaves de criptografia, não a troca de senhas.

**❌ Incorreta D:** O CloudWatch monitora recursos, mas não gerencia credenciais.

</details>

---

## 🎯 Gatilho de Exame

Associe rapidamente cada cenário ao serviço correspondente:

- **Quem realizou uma ação na conta?** → **AWS CloudTrail**
- **Dados sensíveis (PII) no Amazon S3** → **Amazon Macie**
- **Rotação automática de senhas e segredos** → **AWS Secrets Manager**
- **Relatórios SOC, ISO e PCI DSS** → **AWS Artifact**
- **Vulnerabilidades, CVEs e exposição de rede** → **Amazon Inspector**
- **Detecção de ameaças e comportamento suspeito** → **Amazon GuardDuty**
- **Acesso do EC2 ao S3 sem Access Keys** → **IAM Role**
- **Proteção avançada contra DDoS + DRT** → **AWS Shield Advanced**
- **Proteção contra SQL Injection, XSS e regras HTTP** → **AWS WAF**

> **Sinal de Alerta:** Se o enunciado mencionar **"quem fez a ação"**, pense imediatamente em **CloudTrail**. Se falar em **"o recurso está vulnerável"**, pense em **Inspector**. Se falar em **"atividade suspeita acontecendo agora"**, pense em **GuardDuty**.

---

### 🧭 Navegação de Conteúdos

- [🏠 Menu Principal](../README.md)
- [⬅️ Módulo 2: Lab: Configurando Políticas IAM e MFA](13-lab-configurando-politicas-iam-e-mfa.md)
- [➡️ Módulo 3: Amazon EC2 - Instâncias Virtuais na Prática](../03-computacao-e-containers/00-ec2-instancias-virtuais.md)

---