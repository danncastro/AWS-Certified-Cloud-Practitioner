EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '04-armazenamento-e-transferencia/', arquivo '01-s3-classes-de-armazenamento-e-ciclo-vida.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código. 

Mano, papo reto: vamos para o segundo arquivo do Módulo 04! Quero que você gere o conteúdo completo focado nas Classes de Armazenamento do Amazon S3 e Regras de Ciclo de Vida para o arquivo:
👉 '04-armazenamento-e-transferencia/01-s3-classes-de-armazenamento-e-ciclo-vida.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente as principais classes de armazenamento do Amazon S3 exigidas na prova, destacando o equilíbrio entre frequência de acesso, tempo de recuperação e custo:
   - S3 Standard: Alta performance para dados acessados com frequência.
   - S3 Intelligent-Tiering: Movimentação automática de dados entre camadas de acesso frequente e infrequente sem impacto operacional ou taxas de recuperação.
   - S3 Standard-Infrequent Access (Standard-IA) e S3 One Zone-IA: Para dados menos acessados, mas que exigem disponibilidade imediata (com a ressalva de que a One Zone fica em uma única AZ e tem menor proteção contra desastres físicos).
   - S3 Glacier Instant Retrieval, Flexible Retrieval e Deep Archive: Camadas voltadas para arquivamento de longo prazo com tempos de recuperação que variam de milissegundos a horas, oferecendo os menores custos do mercado.
2. Explique o conceito de **S3 Lifecycle Management (Políticas de Ciclo de Vida)**: Regras automatizadas para transicionar objetos entre as classes de armazenamento ao longo do tempo ou excluí-los automaticamente após um período especificado.
3. Crie um guia de decisão rápida para a prova baseado em cenários corporativos de acesso a dados.
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "S3 Storage Classes", "S3 Intelligent-Tiering", "Standard-IA", "One Zone-IA", "S3 Glacier Instant / Flexible / Deep Archive", "Lifecycle configuration rules", "Cost optimization".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!