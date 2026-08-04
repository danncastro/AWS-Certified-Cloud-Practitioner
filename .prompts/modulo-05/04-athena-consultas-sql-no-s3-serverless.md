EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '05-bancos-de-dados-e-analytics/', arquivo '04-athena-consultas-sql-no-s3-serverless.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código. 

Mano, papo reto: vamos para o quinto arquivo do Módulo 05! Quero que você gere o conteúdo completo focado no Amazon Athena para o arquivo:
👉 '05-bancos-de-dados-e-analytics/04-athena-consultas-sql-no-s3-serverless.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o **Amazon Athena** como um serviço de consulta interativa sem servidores (serverless) projetado para analisar dados armazenados no Amazon S3 usando consultas SQL padrão.
2. Destaque as principais características cobradas na prova:
   - Arquitetura serverless nativa: nenhum infraestrutura para gerenciar, provisionar ou configurar; basta apontar para o S3 e rodar queries.
   - Modelo de cobrança pay-as-you-go baseado estritamente na quantidade de dados escaneados por consulta (bytes scanned).
   - Integração direta com o Amazon S3 servindo como data lake subjacente.
3. Explique os casos de uso ideais, como análises ad-hoc de logs, relatórios rápidos e consultas em dados estruturados ou semi-estruturados (CSV, JSON, Parquet) sem precisar carregar os dados para um banco dedicado.
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Amazon Athena", "Serverless query service", "Query data in Amazon S3 using SQL", "Pay per query scanned", "Ad-hoc analytics".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!