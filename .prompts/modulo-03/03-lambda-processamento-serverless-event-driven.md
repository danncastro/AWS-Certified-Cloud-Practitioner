EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '03-computacao-e-containers/', arquivo '03-lambda-processamento-serverless-event-driven.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o quarto arquivo do Módulo 03! Quero que você gere o conteúdo completo focado em Computação Serverless com AWS Lambda para o arquivo:
👉 '03-computacao-e-containers/03-lambda-processamento-serverless-event-driven.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o AWS Lambda como um serviço de computação Serverless (sem servidor) que permite executar código sem provisionar ou gerenciar instâncias de servidores virtuais (EC2).
2. Explique os pilares fundamentais do modelo Serverless e do Lambda cobrados na prova:
   - Escalabilidade automática instantânea (escala de zero para milhares de execuções simultâneas conforme a demanda).
   - Modelo de cobrança baseado no consumo real (paga-se apenas pelos milissegundos de computação utilizados, sem custos quando o código está ocioso).
   - Arquitetura orientada a eventos (Event-Driven), onde o código é disparado em resposta a eventos gerados por serviços AWS (ex: upload de um arquivo no S3, inserção de dados no DynamoDB, requisições HTTP via API Gateway).
3. Destaque as principais limitações e características técnicas que caem em questões de dimensionamento (ex: tempo máximo de execução por requisição de 15 minutos).
4. Crie um comparativo rápido entre EC2 (controle total, gerenciamento de SO, patches e capacidade contínua) vs Lambda (foco exclusivo no código, zero infraestrutura para gerenciar, execução efêmera).
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "AWS Lambda", "Serverless computing", "Event-driven architecture", "Pay-as-you-go pricing model", "Automatic scaling", "Zero server management", "15-minute execution timeout".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!