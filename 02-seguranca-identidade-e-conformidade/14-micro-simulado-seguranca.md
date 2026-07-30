# Micro-Simulado: Segurança, Identidade e Conformidade

O domínio de segurança é um dos mais pesados da prova CLF-C02. A AWS quer ter certeza de que você não vai ser o dev que deixa a chave do cofre pendurada na maçaneta. Este simulado foca nos "duelos" de serviços que a banca adora usar para te confundir. 

Resolva as questões abaixo e sinta se o seu mindset de segurança está afiado.

---

## Questões

### 1. Uma aplicação rodando em uma instância Amazon EC2 precisa acessar arquivos dentro de um bucket do Amazon S3. Seguindo as melhores práticas de segurança, qual método deve ser usado para fornecer esse acesso?
A) Criar um **IAM User** e salvar as **Access Keys** no código-fonte da aplicação.
B) Anexar uma **IAM Role** com permissões adequadas à instância EC2.
C) Habilitar o acesso de leitura pública na **Bucket Policy** do S3.
D) Usar a conta **Root** da AWS para executar a aplicação no EC2.

**Gabarito Comentado:**
*   **Correta: B.** O uso de **IAM Roles** fornece credenciais temporárias para o serviço (EC2), eliminando o risco de chaves fixas vazarem. É o padrão ouro de segurança.
*   **Incorreta A:** Salvar chaves no código (hardcoded) é um erro grave de segurança.
*   **Incorreta C:** Tornar o bucket público expõe dados para toda a internet, violando o privilégio mínimo.
*   **Incorreta D:** Nunca use a conta Root para tarefas diárias ou aplicações.

---

### 2. Um arquiteto de soluções precisa proteger uma aplicação web contra ataques massivos de negação de serviço distribuída (DDoS). Além disso, ele quer ter acesso a um time de resposta especializado (DRT) durante ataques ativos. Qual serviço deve ser contratado?
A) AWS WAF.
B) AWS Shield Standard.
C) AWS Shield Advanced.
D) Amazon GuardDuty.

**Gabarito Comentado:**
*   **Correta: C.** O **Shield Advanced** é a versão paga que oferece mitigação robusta contra DDoS e o benefício exclusivo de suporte do **DDoS Response Team (DRT)**.
*   **Incorreta A:** O WAF é um firewall de aplicação (Layer 7) que filtra tráfego (SQL Injection), mas não é o serviço primário contra DDoS volumétrico.
*   **Incorreta B:** O Shield Standard é gratuito e automático, mas não oferece o suporte do time DRT nem proteção financeira.
*   **Incorreta D:** O GuardDuty apenas detecta ameaças, ele não mitiga ataques DDoS.

---

### 3. Após um incidente de segurança, o time de auditoria da empresa precisa descobrir "quem" deletou uma instância EC2 crítica, "quando" isso aconteceu e de qual "endereço IP" veio a requisição. Qual serviço fornece esse histórico de chamadas de API?
A) Amazon CloudWatch.
B) AWS CloudTrail.
C) AWS Config.
D) Amazon Inspector.

**Gabarito Comentado:**
*   **Correta: B.** O **CloudTrail** é o serviço de auditoria. Ele registra o "quem, o quê, quando e de onde" de todas as chamadas de API feitas na conta.
*   **Incorreta A:** O CloudWatch foca em performance (CPU, logs de app), não em rastreio de ações de usuários/API.
*   **Incorreta C:** O Config foca no histórico de configuração do recurso (como ele mudou), não em quem apertou o botão na API.
*   **Incorreta D:** O Inspector caça vulnerabilidades em softwares instalados.

---

### 4. Uma startup quer automatizar a busca por vulnerabilidades de software e portas abertas não intencionais em suas instâncias EC2 e imagens de contêiner no Amazon ECR. Qual serviço realiza esse escaneamento preventivo?
A) Amazon GuardDuty.
B) Amazon Inspector.
C) AWS WAF.
D) Amazon Macie.

**Gabarito Comentado:**
*   **Correta: B.** O **Inspector** é focado em gerenciamento de vulnerabilidades (CVEs) e acessibilidade de rede no EC2 e ECR.
*   **Incorreta A:** O GuardDuty usa ML para detectar ameaças ativas (ex: mineração de cripto), não é um scanner de vulnerabilidades de pacotes.
*   **Incorreta C:** O WAF filtra tráfego web, ele não olha para dentro do servidor em busca de patches desatualizados.
*   **Incorreta D:** O Macie é exclusivo para caçar dados sensíveis (PII) no S3.

---

### 5. Um banco digital precisa garantir que nenhum bucket do Amazon S3 contenha informações de identificação pessoal (PII), como números de CPF ou cartões de crédito, expostos sem criptografia. Qual serviço automatiza essa descoberta usando Machine Learning?
A) Amazon Macie.
B) Amazon GuardDuty.
C) AWS KMS.
D) AWS Artifact.

**Gabarito Comentado:**
*   **Correta: A.** O **Amazon Macie** é o especialista em privacidade de dados no S3, classificando e protegendo **PII**.
*   **Incorreta B:** O GuardDuty monitora comportamentos maliciosos na conta, não o conteúdo de arquivos no S3.
*   **Incorreta C:** O KMS gerencia chaves de criptografia, mas não "lê" o dado para saber se é um CPF.
*   **Incorreta D:** O Artifact é apenas um portal para baixar PDFs de relatórios de auditoria.

---

### 6. Um auditor de conformidade externa solicitou o relatório SOC 2 e a certificação ISO da infraestrutura física da AWS para validar o compliance da empresa. Onde o usuário pode baixar esses documentos sob demanda?
A) AWS CloudTrail.
B) AWS Trusted Advisor.
C) AWS Artifact.
D) AWS Secrets Manager.

**Gabarito Comentado:**
*   **Correta: C.** O **AWS Artifact** é o portal de autoatendimento para documentos de conformidade, relatórios de auditoria de terceiros e acordos legais.
*   **Incorreta A:** O CloudTrail registra logs de API, não fornece certificados ISO.
*   **Incorreta B:** O Trusted Advisor dá recomendações de otimização, não relatórios de conformidade regulatória.
*   **Incorreta D:** O Secrets Manager guarda senhas, não documentos de auditoria.

---

### 7. Uma empresa quer aumentar a segurança de seu banco de dados Amazon RDS trocando a senha de acesso a cada 30 dias de forma automática, sem intervenção manual. Qual serviço suporta essa rotação nativa?
A) AWS Systems Manager Parameter Store.
B) AWS Secrets Manager.
C) AWS KMS.
D) Amazon CloudWatch.

**Gabarito Comentado:**
*   **Correta: B.** O **Secrets Manager** tem como principal diferencial a **rotação automática de segredos**, integrando-se nativamente com o RDS via Lambda.
*   **Incorreta A:** O Parameter Store armazena configurações e segredos simples (SecureString), mas não possui a funcionalidade de rotação automática nativa.
*   **Incorreta C:** O KMS criptografa os dados, mas não gerencia a lógica de troca da senha no banco de dados.
*   **Incorreta D:** O CloudWatch apenas monitoraria se houvesse erro de login, mas não trocaria a senha.

---

## 🎯 Gatilho de Exame

Mano, para não errar nunca mais, decore estas associações de 1 segundo:

*   **"Quem deletou o recurso?"** ➔ **CloudTrail**.
*   **"Dados sensíveis / PII no S3"** ➔ **Amazon Macie**.
*   **"Troca automática de senha (RDS)"** ➔ **Secrets Manager**.
*   **"Baixar relatório SOC/ISO/PCI"** ➔ **AWS Artifact**.
*   **"Vulnerabilidades / CVE / Portas abertas"** ➔ **Amazon Inspector**.
*   **"Mineração de cripto / Comportamento anômalo / ML"** ➔ **Amazon GuardDuty**.
*   **"Acesso do EC2 ao S3 sem chaves"** ➔ **IAM Role**.
*   **"Ataque DDoS / DRT Team"** ➔ **Shield Advanced**.
*   **"SQL Injection / Camada 7 / Bloqueio de IP"** ➔ **AWS WAF**.

Se o enunciado falar em **"Menor Esforço Operacional"** para conformidade, sempre procure pelo serviço **Gerenciado** que resolve o problema (ex: Secrets Manager em vez de script manual). Marcha!

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Lab: Configurando Políticas IAM e MFA](13-lab-configurando-politicas-iam-e-mfa.md)
* [➡️ Modulo3]()

---
---