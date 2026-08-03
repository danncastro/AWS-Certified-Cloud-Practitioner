EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '05-bancos-de-dados-e-analytics/', arquivo '01-aurora-performance-e-resiliencia-nativa.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o segundo arquivo do Módulo 05! Quero que você gere o conteúdo completo focado no Amazon Aurora para o arquivo:
👉 '05-bancos-de-dados-e-analytics/01-aurora-performance-e-resiliencia-nativa.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o Amazon Aurora como um banco de dados relacional compatível com MySQL e PostgreSQL, desenvolvido nativamente para a nuvem para combinar a velocidade e confiabilidade de bancos de dados comerciais tradicionais de alto padrão com a simplicidade e custo acessível de bancos de código aberto.
2. Destaque os diferenciais arquiteturais brutais cobrados na prova:
   - Performance superior: Até 5 vezes mais rápido que o MySQL padrão e até 3 vezes mais rápido que o PostgreSQL padrão.
   - Armazenamento com tolerância a falhas nativa: O volume do Aurora cresce automaticamente (de 10 GB até 128 TB) e replica cópias dos dados em **6 locais diferentes distribuídos por 3 Zonas de Disponibilidade (AZs)**.
   - Escalabilidade de leitura com Aurora Replicas: Suporte a até 15 réplicas de leitura com failover quase instantâneo.
3. Explique o conceito de **Aurora Serverless**: A opção de computação sob demanda e de autoescala para aplicativos com cargas de trabalho imprevisíveis ou intermitentes, onde o banco escala os recursos de computação automaticamente para cima ou para zero.
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Amazon Aurora", "Cloud-native relational database", "Six copies of data across three AZs", "Aurora Serverless", "High performance database", "Automatic scaling storage".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!