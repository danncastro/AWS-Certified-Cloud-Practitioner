EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '08-arquitetura-e-adocao-aws-caf/', arquivo '03-alta-disponibilidade-az-vs-disaster-recovery-region.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código. 

Mano, papo reto: vamos para o quarto arquivo do Módulo 08! Quero que você gere o conteúdo completo focado em alta disponibilidade (Multi-AZ) versus recuperação de desastres (Multi-Region) para o arquivo:
👉 '08-arquitetura-e-adocao-aws-caf/03-alta-disponibilidade-az-vs-disaster-recovery-region.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente os conceitos fundamentais de resiliência na nuvem e a diferença entre **Fault Tolerance (Tolerância a Falhas)**, **High Availability (Alta Disponibilidade)** e **Disaster Recovery (Recuperação de Desastres)**.
2. Detalhe o escopo de **Multi-AZ (Zonas de Disponibilidade)**:
   - Como a distribuição de instâncias e dados por múltiplas AZs protege contra quedas de datacenters locais com failover automático e RTO/RPO próximos de zero.
3. Detalhe o escopo de **Multi-Region (Regiões da AWS)**:
   - Como a replicação de dados e infraestrutura entre regiões geográficas distintas protege contra desastres em larga escala (ex: interrupções regionais de grande proporção).
4. Explique os conceitos de **RTO (Recovery Time Objective)** e **RPO (Recovery Point Objective)** de forma didática para a prova.
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciis em inglês como "High availability Multi-AZ", "Disaster recovery Multi-Region", "RTO and RPO metrics", "Fault tolerant architecture".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!