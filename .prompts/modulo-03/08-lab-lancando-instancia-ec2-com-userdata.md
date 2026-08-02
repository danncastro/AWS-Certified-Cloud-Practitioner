EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '03-computacao-e-containers/', arquivo '08-lab-lancando-instancia-ec2-com-userdata.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código. 

Mano, papo reto: vamos para o penúltimo arquivo do Módulo 03, o nosso Lab Prático de Computação! Quero que você gere o conteúdo completo focado em passo a passo prático para o arquivo:
👉 '03-computacao-e-containers/08-lab-lancando-instancia-ec2-com-userdata.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Monte um guia mão na massa estruturado e fácil de seguir para o estudante executar no AWS Free Tier / Console AWS.
2. Defina os objetivos do laboratório:
   - Selecionar uma AMI Linux adequada (ex: Amazon Linux 2023).
   - Escolher o tipo de instância elegível para o Free Tier (t2.micro ou t3.micro).
   - Configurar as regras de rede (Security Group liberando as portas 22 para SSH e 80 para HTTP).
   - Inserir um script de **User Data** (Bash) que roda automaticamente no primeiro boot para atualizar o sistema, instalar o servidor web Apache (httpd) e criar uma página HTML personalizada exibindo a identidade da instância.
3. Apresente o bloco de código do script User Data de forma clara e explicada linha por linha.
4. Adicione uma verificação de validação (copiar o IP público da instância, colar no navegador e confirmar que a página web do Apache está rodando perfeitamente).
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos e ações em inglês como "EC2 Launch wizard", "User Data script execution", "Apache web server setup", "Security Group HTTP port 80", "First boot automation".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!