EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '02-seguranca-identidade-e-conformidade/', arquivo '07-deteccao-de-ameacas-guardduty-ml-vs-inspector-vuln.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico established.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o oitavo arquivo do Módulo 02! Quero que você gere o conteúdo completo sobre Detecção de Ameaças e Vulnerabilidades para o arquivo:
👉 '02-seguranca-identidade-e-conformidade/07-deteccao-de-ameacas-guardduty-ml-vs-inspector-vuln.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o Amazon GuardDuty como um serviço de detecção inteligente e contínua de ameaças que utiliza Machine Learning e fontes de dados da AWS (AWS CloudTrail events, VPC Flow Logs, DNS Logs, EKS audit logs) para identificar atividades maliciosas ou não autorizadas (ex: instâncias minerando criptomoedas ou credenciais comprometidas).
2. Apresente o Amazon Inspector como um serviço automatizado de gerenciamento de vulnerabilidades que escaneia proativamente workloads (instâncias EC2, imagens de contêiner no Amazon ECR e funções AWS Lambda) em busca de vulnerabilidades de software conhecidas (CVEs) e desvios de segurança.
3. Monte uma Tabela Comparativa direta ("Duelo de Segurança") para blindar o estudante contra pegadinhas:
   - Amazon GuardDuty = Detecção de ameaças em tempo real / Análise comportamental com ML / monitora logs de rede e API.
   - Amazon Inspector = Varredura de vulnerabilidades em código/SO / pacotes desatualizados / escaneamento de pacotes e imagens.
4. Explique como os dois serviços se complementam na prática de SecOps.
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Amazon GuardDuty", "Amazon Inspector", "Threat detection", "Machine Learning (ML) threat analysis", "Vulnerability management/assessment", "CVE scanning", "Unusual account activity".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!