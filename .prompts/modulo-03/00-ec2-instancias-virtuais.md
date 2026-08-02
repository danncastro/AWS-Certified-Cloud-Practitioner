EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '03-computacao-e-containers/', arquivo '00-ec2-instancias-virtuais.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos iniciar o Módulo 03 focado em Computação e Containers! Quero que você gere o conteúdo completo sobre o serviço carro-chefe de computação para o arquivo:
👉 '03-computacao-e-containers/00-ec2-instancias-virtuais.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o Amazon EC2 (Elastic Compute Cloud) como o serviço de servidores virtuais (instâncias) redimensionáveis na nuvem AWS, eliminando a necessidade de investir em hardware físico inicial (CapEx vs OpEx).
2. Explique os componentes fundamentais de uma instância EC2 que a prova cobra:
   - AMIs (Amazon Machine Images): A imagem base que contém o sistema operacional e as configurações iniciais.
   - Instance Types (Famílias e tamanhos): CPU, memória, capacidade de rede e armazenamento (General Purpose, Compute Optimized, Memory Optimized, Storage Optimized).
   - Key Pairs: Chaves criptográficas para acesso seguro via SSH/RDP.
   - Security Groups: O firewall virtual a nível de instância (stateful).
   - EBS Volumes: O armazenamento em disco acoplado (Elastic Block Store).
3. Explique o conceito de User Data (Dados do Usuário): Scripts que rodam automaticamente no primeiro boot da instância para automatizar instalações e configurações.
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Amazon EC2", "AMI (Amazon Machine Image)", "Instance types", "User Data script", "Virtual servers in the cloud", "Security Groups".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!