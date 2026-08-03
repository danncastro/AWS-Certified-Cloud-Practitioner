EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '04-armazenamento-e-transferencia/', arquivo '06-nuvem-hibrida-storage-gateway.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código. 

Mano, papo reto: vamos para o sétimo arquivo do Módulo 04! Quero que você gere o conteúdo completo focado em AWS Storage Gateway e arquitetura de nuvem híbrida para o arquivo:
👉 '04-armazenamento-e-transferencia/06-nuvem-hibrida-storage-gateway.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o conceito de nuvem híbrida e o papel do **AWS Storage Gateway** como um serviço que conecta aplicativos locais (on-premises) ao armazenamento baseado em nuvem da AWS de forma segura, oferecendo baixa latência através de cache local.
2. Explique os principais tipos de Gateways cobrados na prova:
   - S3 File Gateway: Permite que aplicativos locais acessem arquivos armazenados no Amazon S3 usando protocolos padrão de mercado (NFS ou SMB).
   - Volume Gateway: Fornece armazenamento em bloco para aplicativos locais usando volumes iSCSI (com opções armazenadas em cache ou cópias integrais locais).
   - Tape Gateway: Substitui bibliotecas de fitas físicas locais por fitas virtuais armazenadas de forma segura e econômica no Amazon S3 e S3 Glacier.
3. Crie um cenário de prova clássico onde o Storage Gateway é a resposta definitiva para empresas que querem migrar backups ou dados para o S3 sem alterar a infraestrutura local existente.
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "AWS Storage Gateway", "Hybrid cloud storage", "S3 File Gateway", "Volume Gateway (iSCSI)", "Tape Gateway", "On-premises integration", "Local caching".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!