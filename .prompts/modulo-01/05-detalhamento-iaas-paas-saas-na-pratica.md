EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '01-fundamentos-e-infraestrutura-global/', arquivo '06-detalhamento-iaas-paas-saas-na-pratica.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o sexto arquivo do Módulo 01! Quero que você gere o conteúdo completo mapeando os modelos de serviço de nuvem para o arquivo:
👉 '01-fundamentos-e-infraestrutura-global/06-detalhamento-iaas-paas-saas-na-pratica.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Explique o conceito de IaaS (Infrastructure as a Service): O nível mais básico de controle. Você gerencia o Sistema Operacional, runtime e dados. A AWS cuida do hardware e rede física. Vincule diretamente ao Amazon EC2.
2. Explique o conceito de PaaS (Platform as a Service): Remove a necessidade de gerenciar o SO e a infraestrutura subjacente (patches, provisionamento). Você foca apenas no deploy do código e dados. Vincule diretamente ao AWS Elastic Beanstalk.
3. Explique o conceito de SaaS (Software as a Service): Produto completo, gerenciado de ponta a ponta pelo provedor. Você só usa a interface/software. Vincule a serviços finais como AWS Marketplace (softwares de terceiros) ou ferramentas como o Amazon QuickSight (BI).
4. Crie um paralelo direto ligando o nível de gerenciamento do cliente com flexibilidade (Mais controle/IaaS = Menos automação da AWS; Menos controle/PaaS e SaaS = Maior foco no negócio e menor overhead operacional).
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Infrastructure as a Service (IaaS)", "Platform as a Service (PaaS)", "Software as a Service (SaaS)", "Highest level of flexibility", "Reduce operational overhead", "Manage the underlying infrastructure".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!