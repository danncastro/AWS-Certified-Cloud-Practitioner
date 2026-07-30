EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '02-seguranca-identidade-e-conformidade/', arquivo '13-lab-configurando-politicas-iam-e-mfa.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o décimo quarto arquivo do Módulo 02, o nosso Lab Prático! Quero que você gere o conteúdo completo focado em passo a passo prático para o arquivo:
👉 '02-seguranca-identidade-e-conformidade/13-lab-configurando-politicas-iam-e-mfa.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Monte um guia mão na massa estruturado e fácil de seguir para o estudante executar no AWS Free Tier / Console AWS.
2. Defina os objetivos do laboratório:
   - Criar um IAM User com acesso ao Console da AWS.
   - Criar um IAM Group (ex: "Developers-Group") e adicionar o usuário a ele.
   - Criar uma IAM Policy customizada em JSON aplicando o Princípio do Menor Privilégio (ex: permissão de leitura apenas em buckets S3 específicos).
   - Anexar a policy ao grupo.
   - Configurar o MFA (Multi-Factor Authentication) para o usuário usando um app autenticador (Google Authenticator ou Authy).
3. Apresente os blocos de código JSON das políticas no lab de forma clara e explicada linha por linha.
4. Adicione uma verificação de validação (como testar o login sem MFA ou testar a tentativa de acesso a um serviço não autorizado para ver o "Access Denied").
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos e ações em inglês como "IAM Policy visual editor", "Attach policy to group", "Virtual MFA device", "Access Denied", "Principle of least privilege in practice".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!