EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '04-armazenamento-e-transferencia/', arquivo '07-tabela-objeto-s3-bloco-ebs-arquivo-efs.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o oitavo arquivo do Módulo 04! Quero que você gere o conteúdo completo focado na tabela comparativa entre S3, EBS e EFS para o arquivo:
👉 '04-armazenamento-e-transferencia/07-tabela-objeto-s3-bloco-ebs-arquivo-efs.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Monte uma introdução direta explicando por que a prova CLF-C02 explora intensamente as fronteiras conceituais entre Armazenamento de Objetos, Blocos e Arquivos.
2. Crie uma Tabela Comparativa Abrangente cruzando os critérios cruciais:
   - Amazon S3: Armazenamento de Objetos, escopo Global (Buckets) / Regional, acesso via API/HTTP, ideal para backups, arquivos estáticos, data lakes e mídias.
   - Amazon EBS: Armazenamento em Bloco (Block Storage), escopo de Zona de Disponibilidade (1 AZ por volume), acoplado a instâncias EC2, ideal para sistemas operacionais e bancos de dados transacionais.
   - Amazon EFS: Armazenamento de Arquivos Compartilhado (File Storage / NFS), escopo Multi-AZ Regional, acessado simultaneamente por centenas de instâncias, ideal para CMS (WordPress), diretórios home e compartilhamento corporativo.
3. Adicione uma seção de "Regras de Ouro para Decisão em Questões" com frases diretas no formato "Se a questão falar [Cenário], a tecnologia correta é [S3/EBS/EFS]".
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Object storage vs Block storage vs File storage", "Storage comparison matrix", "Architectural scoping rules", "Exam decision shortcuts".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!