EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '05-bancos-de-dados-e-analytics/', arquivo '00-rds-banco-relacional-gerenciado-sql.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos iniciar o Módulo 05 focado em Bancos de Dados e Analytics! Quero que você gere o conteúdo completo sobre o Amazon RDS para o arquivo:
👉 '05-bancos-de-dados-e-analytics/00-rds-banco-relacional-gerenciado-sql.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o Amazon RDS (Relational Database Service) como um serviço de banco de dados relacional gerenciado que automatiza tarefas complexas como provisionamento, aplicação de patches, backups e recuperação.
2. Liste os motores de banco de dados suportados pelo RDS e exigidos na prova: PostgreSQL, MySQL, MariaDB, Oracle, Microsoft SQL Server e o Amazon Aurora.
3. Explique os dois conceitos arquiteturais fundamentais cobrados exaustivamente na prova:
   - Multi-AZ Deployment: Focado em alta disponibilidade (High Availability) e failover automático para uma standby database em outra zona em caso de queda.
   - Read Replicas (Réplicas de Leitura): Focadas em escalabilidade de leitura (Read Scalability), permitindo distribuir o tráfego de consultas pesadas em instâncias secundárias assíncronas.
4. Explique a estratégia de backups automáticos (Automated Backups) com retenção configurável e os snapshots manuais (DB Snapshots).
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Amazon RDS", "Managed relational database", "Multi-AZ deployment", "Read replicas", "Automated backups", "High availability vs Read scalability".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!