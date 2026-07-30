EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '02-seguranca-identidade-e-conformidade/', arquivo '06-auditoria-e-logs-cloudtrail-quem-fez-o-que.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o sétimo arquivo do Módulo 02! Quero que você gere o conteúdo completo sobre Auditoria e Governança com AWS CloudTrail para o arquivo:
👉 '02-seguranca-identidade-e-conformidade/06-auditoria-e-logs-cloudtrail-quem-fez-o-que.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o AWS CloudTrail como o serviço essencial de auditoria, governança e conformidade da AWS. Ele registra e rastreia todas as chamadas de API e ações realizadas no ambiente (via Console, CLI, SDK ou serviços internos).
2. Destaque a pergunta de ouro que o CloudTrail responde para a equipe de segurança: "Quem fez a ação? Qual API foi chamada? Qual recurso foi afetado? Quando aconteceu? De qual endereço IP veio a requisição?".
3. Explique os conceitos-chave do serviço:
   - Event History: Histórico padrão gratuito dos últimos 90 dias de eventos de gerenciamento.
   - Trails: Configuração para gravar e persistir logs de forma contínua dentro de um bucket do Amazon S3 (para armazenamento de longo prazo) ou CloudWatch Logs.
   - CloudTrail Insights: Recurso para detectar automaticamente comportamentos incomuns e anomalias nas chamadas de API (ex: pico anormal de criação de instâncias ou tentativas de acesso).
4. Faça uma diferenciação explícita para evitar a pegadinha clássica de prova:
   - AWS CloudTrail = Auditoria de chamadas de API / Ações de usuários ("Who did what?").
   - Amazon CloudWatch = Performance, métricas de hardware/sistema e logs da aplicação ("How is the system performing?").
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "AWS CloudTrail", "API call history", "Governance and compliance", "Audit logs", "User activity tracking", "CloudTrail Insights", "CloudTrail vs CloudWatch".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!