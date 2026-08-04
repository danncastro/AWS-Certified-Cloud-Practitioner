EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '06-redes-e-conectividade/', arquivo '00-vpc-rede-privada-virtual-isolada.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos iniciar o Módulo 06 focado em Redes e Conectividade! Quero que você gere o conteúdo completo sobre o Amazon VPC para o arquivo:
👉 '06-redes-e-conectividade/00-vpc-rede-privada-virtual-isolada.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o Amazon VPC (Virtual Private Cloud) como o serviço fundamental que permite provisionar uma seção isolada e logicamente definida da nuvem AWS, onde você detém total controle sobre o ambiente de rede (endereçamento IP, criação de sub-redes, tabelas de rotas e gateways de rede).
2. Explique os conceitos fundamentais de endereçamento e escopo cobrados na prova:
   - Escopo Regional: O VPC é um recurso regional (abrange todas as Zonas de Disponibilidade de uma Região AWS).
   - Blocos CIDR (Classless Inter-Domain Routing): O planejamento de faixas de IP (ex: `/16` para a VPC e `/24` para as sub-redes).
3. Destaque o isolamento lógico como a primeira linha de defesa para proteger instâncias EC2, bancos de dados e aplicações corporativas contra acessos externos indesejados.
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Amazon VPC", "Isolated virtual network", "Regional scope", "CIDR block addressing", "Logical isolation".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!