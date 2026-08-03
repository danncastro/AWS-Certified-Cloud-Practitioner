EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '04-armazenamento-e-transferencia/', arquivo '00-s3-armazenamento-de-objetos-api.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos iniciar o Módulo 04 focado em Armazenamento e Transferência! Quero que você gere o conteúdo completo sobre o Amazon S3 para o arquivo:
👉 '04-armazenamento-e-transferencia/00-s3-armazenamento-de-objetos-api.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o Amazon S3 (Simple Storage Service) como um serviço de armazenamento de objetos altamente escalável, durável (99.999999999% de durabilidade / 11 noves) e seguro, acessível via API de qualquer lugar da web.
2. Explique os conceitos fundamentais do S3 cobrados na prova:
   - Buckets: Os contêineres globais para armazenamento de objetos (com nomes globalmente únicos).
   - Objects: Os arquivos armazenados, compostos por dados (payload) e metadados.
   - Keys (Chaves): O nome exclusivo do objeto dentro do bucket que atua como seu caminho/identificador único.
   - Versioning (Versionamento): O mecanismo para preservar, recuperar e restaurar todas as versões de cada objeto armazenado no bucket (proteção contra exclusão ou sobrescrita acidental).
3. Explique os mecanismos básicos de segurança do S3: Block Public Access (bloqueio de acesso público por padrão), ACLs e Bucket Policies baseadas em JSON.
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciis em inglês como "Amazon S3", "Object storage", "Globally unique bucket names", "Eleven nines of durability", "S3 Versioning", "Bucket policies".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!