EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '05-bancos-de-dados-e-analytics/', arquivo '08-tabela-rds-vs-dynamodb-relacional-vs-nosql.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código. 

Mano, papo reto: vamos para o nono arquivo do Módulo 05! Quero que você gere o conteúdo completo focado na tabela comparativa e nos critérios de decisão para o arquivo:
👉 '05-bancos-de-dados-e-analytics/08-tabela-rds-vs-dynamodb-relacional-vs-nosql.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente uma matriz comparativa estruturada detalhando as diferenças cruciais entre **Amazon RDS (Bancos Relacionais)** e **Amazon DynamoDB (Bancos NoSQL)**.
2. Compare os seguintes pilares cobrados na prova:
   - Estrutura de dados (Tabelas com linhas e colunas / Chave-valor e documentos).
   - Flexibilidade de esquema (Schema rígido vs Schema flexível).
   - Escalabilidade (Vertical via redimensionamento de instâncias no RDS vs Horizontal infinita e automática no DynamoDB).
   - Casos de uso ideais (Transações complexas, JOINs e relatórios vs Alta escala de leitura/escrita com chave primária, jogos, carrinhos de compras, metadados).
3. Inclua gatilhos mentais e cenários de tomada de decisão rápida para identificar qual serviço escolher nas questões de arquitetura do exame.
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Relational vs NoSQL", "Amazon RDS use cases", "Amazon DynamoDB use cases", "Schema flexibility", "Horizontal vs vertical scaling".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!