EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '02-seguranca-identidade-e-conformidade/', arquivo '01-iam-roles-e-acesso-temporario.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o segundo arquivo do Módulo 02! Quero que você gere o conteúdo completo focado em IAM Roles e delegação segura de permissões para o arquivo:
👉 '02-seguranca-identidade-e-conformidade/01-iam-roles-e-acesso-temporario.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Explique o conceito de IAM Role (Função): Uma identidade que você pode criar e que possui permissões específicas, mas que NÃO tem senhas ou chaves de acesso de longo prazo associadas. Em vez de ser ligada a uma pessoa, ela é assumida por qualquer um ou qualquer recurso que precise dela.
2. Detalhe o mecanismo do Acesso Temporário (Temporary Credentials): Como as Roles usam o serviço de segurança por trás dos panos (AWS STS) para gerar credenciais de curta duração que expiram sozinhas, eliminando o risco de chaves vazadas no código.
3. Apresente cenários clássicos de uso que caem na prova:
   - Aplicações rodando em instâncias EC2 que precisam ler dados de um bucket S3 (Gatilho clássico de exame: NUNCA coloque chaves de acesso dentro da EC2; anexe uma IAM Role na instância).
   - Acesso Cross-Account: Usuários de uma conta AWS A que precisam acessar recursos de uma conta AWS B de forma segura.
   - Federação de Identidades (Identity Federation): Usuários externos (do Active Directory da empresa ou login do Google) acessando a AWS usando o AWS IAM Identity Center.
4. Faça um comparativo seco e direto para blindar o estudante contra pegadinhas: IAM User (Humano/App fixo, credenciais fixas) vs IAM Role (Serviços/Acesso temporário, credenciais dinâmicas).
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "IAM Role", "Temporary security credentials", "Cross-account access", "Federation/Federated identity", "Assume a role", "EC2 instance profile".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!