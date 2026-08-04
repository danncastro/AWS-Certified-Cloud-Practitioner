EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '06-redes-e-conectividade/', arquivo '01-subnets-publicas-vs-privadas.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o segundo arquivo do Módulo 06! Quero que você gere o conteúdo completo focado em Sub-redes Públicas e Privadas para o arquivo:
👉 '06-redes-e-conectividade/01-subnets-publicas-vs-privadas.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o conceito de sub-redes (subnets) como divisões de IP dentro de uma VPC, detalhando o escopo estrito de Zona de Disponibilidade (1 subnet = 1 AZ).
2. Explique a diferença crucial cobrada na prova entre:
   - Sub-redes Públicas (Public Subnets): Possuem rota direta para a Internet através de um Internet Gateway (IGW), ideais para recursos que precisam ser acessados pelo público (ex: servidores web, load balancers).
   - Sub-redes Privadas (Private Subnets): Não possuem rota direta para a internet, mantendo os recursos isolados e protegidos (ex: bancos de dados, servidores de backend, APIs internas).
3. Explique o papel das tabelas de rotas (Route Tables) para direcionar o tráfego de saída das subnets.
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Public subnets", "Private subnets", "Availability Zone restriction", "Route tables", "Internet-facing architecture".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!