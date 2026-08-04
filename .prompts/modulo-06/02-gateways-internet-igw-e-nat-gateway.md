EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '06-redes-e-conectividade/', arquivo '02-gateways-internet-igw-e-nat-gateway.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o terceiro arquivo do Módulo 06! Quero que você gere o conteúdo completo focado em Internet Gateways e NAT Gateways para o arquivo:
👉 '06-redes-e-conectividade/02-gateways-internet-igw-e-nat-gateway.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o papel dos gateways na arquitetura de rede da AWS, funcionando como pontes de comunicação entre a VPC e redes externas (como a internet).
2. Detalhe os dois componentes vitais cobrados na prova:
   - Internet Gateway (IGW): Componente horizontalmente escalável, redundante e altamente disponível que permite a comunicação entre instâncias na VPC e a internet pública (essencial para sub-redes públicas).
   - NAT Gateway (Network Address Translation): Serviço gerenciado posicionado em uma subnet pública que permite a instâncias em sub-redes privadas iniciarem conexões de saída para a internet (ex: baixar patches ou atualizações), bloqueando totalmente conexões vindas da internet para dentro da subnet privada.
3. Explique o cenário clássico de prova onde um servidor em rede privada precisa de acesso à internet para atualizar pacotes sem se expor a ataques externos.
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Internet Gateway (IGW)", "NAT Gateway", "Outbound internet access", "Private subnet connectivity", "Managed NAT service".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!