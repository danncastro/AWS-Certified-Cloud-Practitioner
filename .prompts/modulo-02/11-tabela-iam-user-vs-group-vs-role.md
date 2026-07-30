EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '02-seguranca-identidade-e-conformidade/', arquivo '11-tabela-iam-user-vs-group-vs-role.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o décimo segundo arquivo do Módulo 02! Quero que você gere o conteúdo completo focado em síntese e comparação cirúrgica para o arquivo:
👉 '02-seguranca-identidade-e-conformidade/11-tabela-iam-user-vs-group-vs-role.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Monte uma introdução direta explicando por que a banca ama tentar trocar User, Group e Role em cenários práticos.
2. Crie uma Tabela Comparativa Completa cobrindo os pilares:
   - Definição / Quem é.
   - Tipo de Credencial (Long-term / Short-term / Nenhuma).
   - Associação com pessoas físicas vs. serviços/aplicações.
   - Regras Especiais e Restrições (Ex: Grupos não podem conter outros grupos; Roles não possuem senhas e usam STS; Users não devem ter credenciais de longo prazo para instâncias).
   - Casos de uso ideais no dia a dia e na prova.
3. Adicione uma seção de "Regras de Ouro para Decisão em Questões" com frases no formato "Se a questão falar [Gatilho], a resposta é [Entidade]".
4. Garanta a seção "🎯 Gatilho de Exame" mapeando os termos chave em inglês como "IAM User", "IAM Group", "IAM Role", "Long-term credentials", "Temporary credentials", "STS (Security Token Service)", "No nested groups".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!