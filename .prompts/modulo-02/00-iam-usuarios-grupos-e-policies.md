EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '02-seguranca-identidade-e-conformidade/', arquivo '00-iam-usuarios-grupos-e-policies.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: inauguramos o Módulo 02 com o pé no acelerador! Quero que você gere o conteúdo completo focado na base do gerenciamento de acessos da AWS para o arquivo:
👉 '02-seguranca-identidade-e-conformidade/00-iam-usuarios-grupos-e-policies.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o AWS IAM (Identity and Access Management) como o serviço gratuito e global (não associado a uma região específica) que controla quem pode autenticar (autenticação) e quais permissões possui (autorização) na conta AWS.
2. Defina explicitamente os conceitos de:
   - IAM User (Usuário): Uma identidade para uma pessoa ou aplicação que interage com a AWS (long-term credentials).
   - IAM Group (Grupo): Uma coleção de usuários IAM. Explique que permissões anexadas ao grupo são herdadas pelos usuários, facilitando o gerenciamento. Enfatize que um grupo NÃO pode conter outros grupos (sem aninhamento).
3. Explique o que são as IAM Policies (Políticas): Documentos em formato JSON que definem explicitamente permissões. Explique de forma muito simples a estrutura básica de uma policy baseada no acrônimo PARC (Principal, Action, Resource, Condition) ou os blocos essenciais: Effect (Allow/Deny), Action (o que pode fazer), Resource (em qual recurso).
4. Introduza o Princípio do Menor Privilégio (Principle of Least Privilege): O conceito de dar apenas o acesso mínimo necessário para o usuário realizar seu trabalho, sendo uma das melhores práticas de segurança mais cobradas no exame.
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Identity and Access Management (IAM)", "IAM User", "IAM Group", "JSON Policy document", "Principle of least privilege", "Global service", "Effect, Action, Resource".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!