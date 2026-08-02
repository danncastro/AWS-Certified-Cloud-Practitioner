EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '03-computacao-e-containers/', arquivo '02-auto-scaling-e-elastic-load-balancing.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o terceiro arquivo do Módulo 03! Quero que você gere o conteúdo completo focado em Elastic Load Balancing e EC2 Auto Scaling para o arquivo:
👉 '03-computacao-e-containers/02-auto-scaling-e-elastic-load-balancing.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o Elastic Load Balancing (ELB) como o serviço gerenciado que distribui automaticamente o tráfego de entrada de aplicações entre múltiplos destinos (como instâncias EC2, contêineres e endereços IP) em várias Zonas de Disponibilidade (AZs).
2. Explique os principais tipos de Load Balancers que caem na prova:
   - Application Load Balancer (ALB): Focado em tráfego HTTP/HTTPS (camada 7), ideal para aplicações web baseadas em rotas e microsserviços.
   - Network Load Balancer (NLB): Focado em tráfego TCP/UDP de altíssima performance e baixíssima latência (camada 4).
   - Classic Load Balancer (CLB): Versão legada (geralmente evitada em novos projetos, mas citada na prova).
3. Apresente o Amazon EC2 Auto Scaling (ASG) como o serviço que garante que você tenha o número correto de instâncias EC2 rodando para lidar com a carga da sua aplicação. Explique seus três conceitos centrais: Minimum capacity, Maximum capacity e Desired capacity.
4. Explique como o Auto Scaling lida com falhas: Se uma instância falha ou trava nas verificações de saúde (Health Checks), o ASG a encerra automaticamente e provisiona uma nova instância no lugar.
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Elastic Load Balancing (ELB)", "Application Load Balancer (ALB)", "Network Load Balancer (NLB)", "EC2 Auto Scaling Group (ASG)", "Health checks", "Scale-out and scale-in", "High availability architecture".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!