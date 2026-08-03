EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '04-armazenamento-e-transferencia/', arquivo '03-efs-sistema-arquivos-compartilhado-nfs.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código. 

Mano, papo reto: vamos para o quarto arquivo do Módulo 04! Quero que você gere o conteúdo completo focado em Amazon EFS (Elastic File System) para o arquivo:
👉 '04-armazenamento-e-transferencia/03-efs-sistema-arquivos-compartilhado-nfs.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o Amazon EFS (Elastic File System) como um sistema de arquivos gerenciado baseado no protocolo NFS (Network File System) que permite o compartilhamento simultáneo de dados entre centenas ou milhares de instâncias EC2.
2. Destaque o grande diferencial cobrado na prova: Enquanto o EBS fica preso a uma única AZ, o EFS possui arquitetura regional, permitindo que instâncias EC2 em **múltiplas Zonas de Disponibilidade** leiam e escrevam nos mesmos arquivos ao mesmo tempo (Ideal para arquiteturas altamente disponíveis).
3. Explique os casos de uso clássicos na prova: Gerenciamento de conteúdo web compartilhado (ex: CMS como WordPress rodando em um cluster de instâncias atrás de um Load Balancer), compartilhamento de diretórios home de usuários, análise de dados e ferramentas de desenvolvimento corporativo.
4. Crie um comparativo rápido de arquitetura: EBS (Block Storage / 1 AZ) vs EFS (File Storage / Multi-AZ) vs S3 (Object Storage / Global).
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Amazon EFS", "Network File System (NFS)", "Multi-AZ file sharing", "Concurrent access", "Shared storage architecture".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!