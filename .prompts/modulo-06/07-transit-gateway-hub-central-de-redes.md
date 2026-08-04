EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '06-redes-e-conectividade/', arquivo '07-transit-gateway-hub-central-de-redes.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o oitavo arquivo do Módulo 06! Quero que você gere o conteúdo completo focado no AWS Transit Gateway para o arquivo:
👉 '06-redes-e-conectividade/07-transit-gateway-hub-central-de-redes.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o problema de escalabilidade de rede gerado pelo uso massivo de VPC Peerings individuais (o modelo de malha pontual onde $N \times (N-1) / 2$ conexões viram um pesadelo de gestão).
2. Apresente o **AWS Transit Gateway** como um serviço de hub central de redes que permite interconectas múltiplas VPCs, contas AWS e redes locais (on-premises) através de um único ponto de controle unificado.
3. Destaque os benefícios estruturais cobrados na prova:
   - Simplificação drástica da arquitetura de rede em estrela (hub-and-spoke).
   - Escalabilidade massiva para centenas de VPCs e conexões híbridas (VPN/Direct Connect).
   - Gerenciamento centralizado de rotas e políticas de tráfego.
4. Crie um cenário clássico de exame contrastando a desordem do VPC Peering ramificado com a elegância centralizada do Transit Gateway para grandes corporações.
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciis em inglês como "AWS Transit Gateway", "Hub-and-spoke network architecture", "Centralized network routing", "VPC peering complexity reduction", "Scalable cloud networking".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!