EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '04-armazenamento-e-transferencia/', arquivo '02-ebs-volumes-em-bloco-disco-virtual.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o terceiro arquivo do Módulo 04! Quero que você gere o conteúdo completo focado em Amazon EBS (Elastic Block Store) para o arquivo:
👉 '04-armazenamento-e-transferencia/02-ebs-volumes-em-bloco-disco-virtual.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o Amazon EBS (Elastic Block Store) como o serviço de armazenamento em bloco (block storage) persistente e de alta performance projetado para uso com instâncias Amazon EC2 (funcionando como um "disco rígido virtual" acoplado à máquina).
2. Destaque o escopo geográfico fundamental cobrado na prova: Um volume EBS está estritamente vinculado a uma única **Zona de Disponibilidade (AZ)**, replicando dados automaticamente dentro daquela AZ para garantir alta durabilidade, mas exigindo snapshots para ser movido para outra AZ.
3. Explique as principais famílias de volumes EBS exigidas no exame:
   - SSD-backed (General Purpose SSD - gp2/gp3 e Provisioned IOPS SSD - io1/io2): Ideais para sistemas operacionais, bancos de dados transacionais (OLTP) e cargas de trabalho que exigem alta taxa de operações de leitura/escrita por segundo (IOPS).
   - HDD-backed (Throughput Optimized HDD - st1 e Cold HDD - sc1): Ideais para grandes volumes de dados sequenciais, data warehouses e arquivos acessados com pouca frequência (nunca use HDD para o sistema operacional ou bancos de dados).
4. Explique a importância vital dos **EBS Snapshots**: Backups incrementais armazenados de forma segura e durável no Amazon S3, usados para backup point-in-time, migração de volumes entre AZs e clonagem de discos.
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Amazon EBS", "Block storage", "Availability Zone scope", "General Purpose SSD (gp3)", "Provisioned IOPS", "EBS Snapshots", "Incremental backups".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!