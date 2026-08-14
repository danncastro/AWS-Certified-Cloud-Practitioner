EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '05-bancos-de-dados-e-analytics/', arquivo '10-lab-criando-banco-rds-multi-az.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02/SAA-C03 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código. 

Mano, papo reto: vamos para o laboratório de Alta Disponibilidade! Quero que você gere o conteúdo prático e explicativo sobre a configuração de um RDS Multi-AZ para o arquivo:
👉 '05-bancos-de-dados-e-analytics/10-lab-criando-banco-rds-multi-az.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o cenário prático: por que e quando ativar Multi-AZ em um RDS (foco em resiliência e recuperação de desastres, não em performance de leitura).
2. Detalhe o passo a passo lógico do laboratório no Console AWS:
   - Escolha do motor (ex: MySQL/PostgreSQL).
   - Configuração de disponibilidade (Seleção da opção "Multi-AZ deployment").
   - Explicação sobre a instância Standby (o que acontece nos bastidores quando ocorre um failover).
3. Diferencie claramente:
   - **Multi-AZ:** Replicação síncrona, foco em alta disponibilidade e failover automático.
   - **Read Replicas:** Replicação assíncrona, foco em escalabilidade de leitura (leitura de dados).
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "RDS Multi-AZ deployment", "Automatic failover to standby instance", "Synchronous replication", "Read replicas vs Multi-AZ for high availability".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!