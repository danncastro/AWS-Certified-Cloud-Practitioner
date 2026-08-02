EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '03-computacao-e-containers/', arquivo '06-tabela-comparativa-familias-instancia-ec2.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o sétimo arquivo do Módulo 03! Quero que você gere o conteúdo completo focado em síntese e comparação das famílias de instâncias EC2 para o arquivo:
👉 '03-computacao-e-containers/06-tabela-comparativa-familias-instancia-ec2.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Monte uma introdução direta explicando por que a banca ama cobrar o mapeamento entre o perfil de uma aplicação corporativa e a família correta de instâncias EC2.
2. Crie uma Tabela Comparativa Completa cobrindo as principais famílias:
   - General Purpose (Uso Geral - ex: série T e M): Equilíbrio entre computação, memória e rede. Ideal para servidores web, microsserviços e ambientes de desenvolvimento.
   - Compute Optimized (Otimizadas para Computação - ex: série C): Alta performance de processamento por vCPU. Ideal para processamento em lote, transcodificação de mídia, jogos e cargas intensivas de CPU.
   - Memory Optimized (Otimizadas para Memória - ex: série R e X): Desempenho rápido para cargas que processam grandes conjuntos de dados em memória. Ideal para bancos de dados relacionais e em memória (como Redis/Memcached) e grandes caches.
   - Storage Optimized (Otimizadas para Armazenamento - ex: série I e D): Altas taxas de transferência de leitura/escrita (IOPS) em discos locais. Ideal para bancos de dados NoSQL (como Cassandra/MongoDB), data warehouses e sistemas de arquivos distribuídos.
   - Accelerated Computing (Computação Acelerada - ex: série P e G): Uso de GPUs para processamento gráfico, machine learning e renderização pesada.
3. Adicione uma seção de "Regras de Ouro para Decisão em Questões" com frases no formato "Se a questão falar [Gatilho de carga de trabalho], a resposta é [Família de Instância]".
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "General Purpose instances", "Compute Optimized instances", "Memory Optimized instances", "Storage Optimized instances", "Accelerated Computing instances", "Workload profiling".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!