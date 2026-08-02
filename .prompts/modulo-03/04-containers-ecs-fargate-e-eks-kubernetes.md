EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '03-computacao-e-containers/', arquivo '04-containers-ecs-fargate-e-eks-kubernetes.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o quinto arquivo do Módulo 03! Quero que você gere o conteúdo completo focado em Contêineres, ECS, EKS e Fargate para o arquivo:
👉 '03-computacao-e-containers/04-containers-ecs-fargate-e-eks-kubernetes.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o conceito de contêineres na AWS e por que eles são populares (empacotamento de aplicações com todas as dependências para rodar de forma consistente em qualquer ambiente).
2. Explique os dois principais serviços de orquestração de contêineres cobrados na prova:
   - Amazon ECS (Elastic Container Service): O orquestrador de contêineres altamente escalável e de alto desempenho desenvolvido nativamente pela AWS.
   - Amazon EKS (Elastic Kubernetes Service): O serviço gerenciado que facilita a execução de Kubernetes na AWS sem precisar gerenciar o plano de controle (control plane) do Kubernetes por conta própria.
3. Detalhe a revolução do AWS Fargate:
   - Explique o conceito de "Serverless para Contêineres". Com o Fargate, você executa contêineres sem precisar provisionar, configurar ou gerenciar instâncias EC2. A AWS cuida de toda a infraestrutura subjacente, dimensionando a computação sob demanda.
4. Monte um resumo comparativo rápido (ECS vs EKS e o papel do Fargate em ambos) para matar as pegadinhas de prova.
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciis em inglês como "Amazon ECS", "Amazon EKS", "AWS Fargate", "Container orchestration", "Serverless containers", "Kubernetes control plane", "Docker container images".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!