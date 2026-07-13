EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '01-fundamentos-e-infraestrutura-global/', arquivo '03-infraestrutura-global-regioes-e-azs.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como) no texto ou no código.

Mano, papo reto: vamos para o terceiro arquivo do Módulo 01! Quero que você gere o conteúdo completo focado na arquitetura física da AWS para o arquivo:
👉 '01-fundamentos-e-infraestrutura-global/03-infraestrutura-global-regioes-e-azs.md'

Diretrizes de Conteúdo para este arquivo:
1. Explique o conceito de Região (Region): uma localização geográfica isolada no mundo que contém múltiplos data centers. Explique os 4 critérios para escolher uma região (Conformidade/Leis de dados, Proximidade/Latência, Disponibilidade de serviços e Custo).
2. Explique o conceito de Zona de Disponibilidade (Availability Zone - AZ): um ou mais data centers discretos com energia, rede e conectividade redundantes dentro de uma Região AWS. Explique que elas são independentes e conectadas por redes de ultra-baixa latência.
3. Detalhe como a arquitetura Multi-AZ protege o sistema contra desastres locais (incêndios, enchentes, quedas de energia) e garante Alta Disponibilidade (High Availability) e Tolerância a Falhas (Fault Tolerance).
4. Traga um cenário prático ou exemplo real de decisão arquitetural (Ex: rodar instâncias EC2 em duas AZs diferentes na Região de São Paulo para aguentar a queda de um data center inteiro).
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "AWS Region", "Availability Zone (AZ)", "Isolated geographic area", "Redundant power and networking", "High availability".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!