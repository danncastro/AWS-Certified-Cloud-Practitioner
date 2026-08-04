EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '06-redes-e-conectividade/', arquivo '06-vpc-peering-e-endpoints-gateway-vs-interface.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o sétimo arquivo do Módulo 06! Quero que você gere o conteúdo completo focado em VPC Peering e VPC Endpoints para o arquivo:
👉 '06-redes-e-conectividade/06-vpc-peering-e-endpoints-gateway-vs-interface.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o conceito de interconexão de redes privadas na AWS, explicando como expandir a comunicação sem expor os dados à internet pública.
2. Detalhe o **VPC Peering**:
   - Conexão de rede direta entre duas VPCs usando seus endereços IP privados.
   - O tráfego permanece inteiramente na rede global da AWS, sem transitar pela internet.
   - Regra de ouro da prova: VPC Peering não é transitivo (se a VPC A se conecta à VPC B, e a VPC B se conecta à VPC C, a VPC A não fala automaticamente com a VPC C sem um peering direto entre elas).
3. Detalhe os **VPC Endpoints** (Interface vs Gateway):
   - Permitem que instâncias em sub-redes privadas acessem serviços da AWS (como Amazon S3, DynamoDB, Systems Manager) sem precisar de um NAT Gateway ou de um Internet Gateway.
   - Gateway Endpoints: Gratuitos, voltados especificamente e suportados apenas para Amazon S3 e Amazon DynamoDB baseados em tabelas de rotas.
   - Interface Endpoints (AWS PrivateLink): Alimentados por ENIs (Elastic Network Interfaces) com IPs privados na subnet, suportados para uma enorme gama de serviços AWS mediante cobrança por hora e por gigabyte.
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "VPC Peering", "Non-transitive peering", "VPC Endpoints", "Gateway endpoints (S3/DynamoDB)", "Interface endpoints (AWS PrivateLink)".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!