EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '02-seguranca-identidade-e-conformidade/', arquivo '03-protecao-contra-ddos-shield-e-waf.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o quarto arquivo do Módulo 02! Quero que você gere o conteúdo completo focado em segurança de borda e mitigação de ataques para o arquivo:
👉 '02-seguranca-identidade-e-conformidade/03-protecao-contra-ddos-shield-e-waf.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o AWS WAF (Web Application Firewall) como um firewall de aplicação focado na Camada 7 (HTTP/HTTPS). Explique que ele protege contra vulnerabilidades web comuns do OWASP Top 10, como SQL Injection (injeção de código malicioso no banco) e Cross-Site Scripting (XSS), permitindo bloquear IPs específicos ou requisições suspeitas usando regras customizáveis (Web ACLs).
2. Apresente o AWS Shield como o serviço focado na proteção contra ataques de negação de serviço (DDoS - Distributed Denial of Service) nas Camadas 3 e 4 (Rede e Transporte).
3. Detalhe explicitamente a diferença entre os dois níveis do Shield que a prova adora cobrar:
   - AWS Shield Standard: Proteção automática e gratuita ativada por padrão para todos os clientes da AWS contra os ataques mais comuns de DDoS.
   - AWS Shield Advanced: Serviço pago e robusto que oferece proteção especializada, suporte 24/7 do time de resposta a DDoS da AWS (DRT - DDoS Response Team) e proteção financeira contra picos de custos gerados por ataques de negação de serviço.
4. Crie uma tabela de comparação rápida de "Quem é Quem" ligando os cenários práticos: Se o enunciado falar em bloquear IPs maliciosos ou ataques como SQL Injection, a resposta é WAF. Se falar em mitigar ataques DDoS em massa ou envolver o DDoS Response Team, a resposta é Shield Advanced.
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "AWS WAF (Web Application Firewall)", "AWS Shield Standard vs Advanced", "DDoS mitigation", "Layer 7 (Application layer)", "SQL Injection and Cross-Site Scripting (XSS)", "DDoS Response Team (DRT)", "Web ACL".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!