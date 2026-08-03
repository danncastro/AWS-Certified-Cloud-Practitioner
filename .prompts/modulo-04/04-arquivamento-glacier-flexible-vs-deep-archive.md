EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '04-armazenamento-e-transferencia/', arquivo '04-arquivamento-glacier-flexible-vs-deep-archive.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutusantes de referência) no texto ou no código.

Mano, papo reto: vamos para o quinto arquivo do Módulo 04! Quero que você gere o conteúdo completo focado em arquivamento de longo prazo com o Amazon S3 Glacier Flexible Retrieval e S3 Glacier Deep Archive para o arquivo:
👉 '04-armazenamento-e-transferencia/04-arquivamento-glacier-flexible-vs-deep-archive.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o propósito do arquivamento de longo prazo na nuvem: reter dados históricos, backups regulatórios e arquivos de auditoria por anos ou décadas com o menor custo de armazenamento possível.
2. Detalhe as duas principais opções de Glacier voltadas para arquivos frios cobradas na prova:
   - Amazon S3 Glacier Flexible Retrieval: Projetado para dados acessados raramente, com opções de recuperação flexíveis que variam de minutos a horas (incluindo opções de recuperação acelerada/Expedited).
   - Amazon S3 Glacier Deep Archive: A classe de armazenamento mais barata da AWS, projetada para dados que podem ser acessados uma ou duas vezes por ano e que aceitam um tempo de recuperação de até 12 horas.
3. Explique os conceitos críticos de retenção e penalidades por exclusão antecipada que a prova adora cobrar (períodos mínimos de armazenamento de 90 dias para Flexible e 180 dias para Deep Archive).
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciis em inglês como "S3 Glacier Flexible Retrieval", "S3 Glacier Deep Archive", "Long-term data archiving", "Compliance retention policies", "Retrieval time options", "Lowest cost cloud storage".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!