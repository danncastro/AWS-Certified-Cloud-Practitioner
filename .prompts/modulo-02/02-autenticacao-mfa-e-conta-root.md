EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '02-seguranca-identidade-e-conformidade/', arquivo '02-autenticacao-mfa-e-conta-root.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o terceiro arquivo do Módulo 02! Quero que você gere o conteúdo completo focado em Conta Root e Melhores Práticas de Proteção para o arquivo:
👉 '02-seguranca-identidade-e-conformidade/02-autenticacao-mfa-e-conta-root.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Explique o conceito de AWS Account Root User (Usuário Root da Conta): A identidade criada automaticamente quando a conta AWS é aberta. Detalhe que ele possui acesso completo e irrestrito a TODOS os recursos e informações de faturamento da conta, e que esse poder não pode ser limitado por nenhuma policy.
2. Destaque as Melhores Práticas de Segurança para a Conta Root exaustivamente cobradas no exame:
   - Trancar as chaves de acesso (Access Keys) da root e nunca criá-las.
   - Usar uma senha extremamente forte.
   - Parar de usar a conta Root para tarefas diárias imediatamente após criar o primeiro usuário administrativo no IAM.
   - Ativar obrigatoriamente o MFA (Multi-Factor Authentication).
3. Explique detalhadamente o Multi-Factor Authentication (MFA): O que é, como ele adiciona uma camada extra de proteção exigindo algo que você sabe (senha) e algo que você possui (um token físico, chave de segurança de hardware ou aplicativo autenticador como Google Authenticator no celular).
4. Cite exemplos pontuais de ações que APENAS o usuário Root consegue fazer e que a prova adora perguntar (como fechar a conta AWS, alterar os planos de suporte ou mudar as configurações de faturamento consolidadas).
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "AWS Account Root User", "Multi-Factor Authentication (MFA)", "Root credentials", "Best practices", "Delete root access keys", "Protect root account".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!