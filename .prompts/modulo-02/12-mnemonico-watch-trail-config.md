EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '02-seguranca-identidade-e-conformidade/', arquivo '12-mnemonico-watch-trail-config.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o décimo terceiro arquivo do Módulo 02! Quero que você gere o conteúdo completo focado em memorização rápida e desambiguação dos serviços de monitoramento/auditoria para o arquivo:
👉 '02-seguranca-identidade-e-conformidade/12-mnemonico-watch-trail-config.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Explique por que a banca tenta ativamente confundir CloudWatch vs CloudTrail vs AWS Config.
2. Apresente um Mnemônico/Regra de Ouro Inesquecível para fixar a responsabilidade de cada um:
   - CloudWATCH = "WATCH the metrics & performance" (Métricas, performance, alarme de uso de CPU, logs de aplicação).
   - CloudTRAIL = "TRAIL of actions" (Trilha de auditoria, chamadas de API, "quem fez o quê e quando").
   - AWS CONFIG = "CONFIGuration history & compliance" (Histórico de alterações de configuração de recursos, conformidade contínua, "como o recurso mudou ao longo do tempo").
3. Crie um cenário prático integrado usando uma única infraestrutura (ex: uma instância EC2 que teve a porta SSH aberta publicamente) mostrando o que CADA UM dos três serviços vai registrar/alertar nesse momento:
   - CloudTrail registra QUEM executou a chamada de API de alteração no Security Group.
   - AWS Config registra QUE a configuração do Security Group mudou e marca o recurso como "Non-compliant".
   - CloudWatch dispara um alarme baseado em logs ou métricas de tráfego se houver pico de acessos.
4. Monte a Tabela Definitiva de Resolução Rápida para a prova.
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Amazon CloudWatch", "AWS CloudTrail", "AWS Config", "Performance metrics", "API call history", "Resource configuration changes", "Compliance tracking".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!