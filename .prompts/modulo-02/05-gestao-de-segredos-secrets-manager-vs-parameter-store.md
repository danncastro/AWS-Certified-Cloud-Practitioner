EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '02-seguranca-identidade-e-conformidade/', arquivo '05-gestao-de-segredos-secrets-manager-vs-parameter-store.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código. 

Mano, papo reto: vamos para o sexto arquivo do Módulo 02! Quero que você gere o conteúdo completo sobre Gerenciamento de Segredos e Configurações para o arquivo:
👉 '02-seguranca-identidade-e-conformidade/05-gestao-de-segredos-secrets-manager-vs-parameter-store.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Explique o problema de deixar segredos (senhas de banco de dados, chaves de API, tokens) hardcoded no código de aplicações e por que centralizar isso em serviços gerenciados é crucial.
2. Apresente o AWS Secrets Manager: Serviço desenhado especificamente para armazenar, gerenciar e criptografar credenciais e segredos complexos. Destaque o diferencial número 1 cobrado na prova: ROTAÇÃO AUTOMÁTICA de segredos usando integração nativa com AWS Lambda e bancos como Amazon RDS.
3. Apresente o AWS Systems Manager Parameter Store (SSM Parameter Store): Serviço para armazenar parâmetros de configuração de sistemas (strings simples, URLs de API, flags, chaves encriptadas SecureString). Destaque que ele tem uma camada gratuita (Standard parameters) e é focado em configurações gerais, mas NÃO possui rotação automática nativa de segredos.
4. Crie uma Tabela Comparativa de Decisão ("Gatilho de Prova"):
   - Se o enunciado falar de rotação automática de senhas de banco de dados (RDS, Redshift), criptografia integrada e ciclo de vida de segredos -> AWS Secrets Manager.
   - Se o enunciado falar de armazenar strings de configuração, chaves/valores genéricos de forma simples, hierárquica e de baixo custo/gratuita -> AWS Systems Manager Parameter Store.
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "AWS Secrets Manager", "AWS Systems Manager Parameter Store (SSM Parameter Store)", "Automatic rotation of secrets", "Hardcoded credentials", "SecureString parameter", "Cost-effective configuration storage".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!