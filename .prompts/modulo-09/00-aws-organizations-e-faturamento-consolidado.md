EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '09-gestao-de-custos-e-governanca/', arquivo '00-aws-organizations-e-faturamento-consolidado.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos iniciar o Módulo 09 focando no gerenciamento centralizado de contas e cobrança! Quero que você gere o conteúdo completo focado no AWS Organizations e Faturamento Consolidado para o arquivo:
👉 '09-gestao-de-custos-e-governanca/00-aws-organizations-e-faturamento-consolidado.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o **AWS Organizations** como um serviço de gerenciamento de contas que permite consolidar e gerenciar centralmente múltiplas contas AWS.
2. Detalhe os conceitos estruturais fundamentais:
   - **Management Account (Payer Account):** A conta principal responsável pelo pagamento e criação da organização.
   - **Member Accounts:** As contas individuais gerenciadas dentro da organização.
   - **Organizational Units (OUs):** Grupos lógicos de contas para aplicar políticas e governança.
3. Detalhe os benefícios e o funcionamento do **Consolidated Billing (Faturamento Consolidado)**:
   - Fatura única unificada para todas as contas membro.
   - Agrupamento de consumo para atingir escalões de desconto por volume (Volume Discounts), como consumo acumulado do S3/EC2.
   - Compartilhamento de descontos de Instâncias Reservadas (RIs) e Savings Plans entre contas da organização.
   - Esclareça que o AWS Organizations é um serviço sem custo adicional (Free feature).
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "AWS Organizations", "Consolidated billing", "Management account / Payer account", "Organizational Units (OUs)", "Volume discounts across accounts", "Sharing Reserved Instances benefits".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!