EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '06-redes-e-conectividade/', arquivo '03-security-groups-stateful-vs-nacls-stateless.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o quarto arquivo do Módulo 06! Quero que você gere o conteúdo completo focado em Security Groups e NACLs para o arquivo:
👉 '06-redes-e-conectividade/03-security-groups-stateful-vs-nacls-stateless.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente as camadas de segurança de rede da AWS, explicando como o tráfego é filtrado em diferentes níveis da infraestrutura.
2. Detalhe o **Security Group**:
   - Funciona como um firewall virtual associado ao nível da **instância EC2** (interface de rede).
   - É **Stateful** (com estado): Se você permitir o tráfego de entrada (inbound), o tráfego de saída correspondente é automaticamente permitido de volta, sem precisar configurar regras de saída.
   - Suporta apenas regras de permissão (allow rules).
3. Detalhe a **Network ACL (NACL)**:
   - Funciona como uma camada de segurança adicional associada ao nível da **Sub-rede (Subnet)**.
   - É **Stateless** (sem estado): O tráfego de entrada e o tráfego de saída devem ser explicitamente permitidos por regras separadas (inbound e outbound).
   - Suporta tanto regras de permissão quanto de negação (allow e deny rules), operando por ordem de número de regra.
4. Monte um comparativo claro destacando quando usar cada uma nas pegadinhas da prova.
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Security Groups", "Network ACLs (NACLs)", "Stateful vs Stateless", "Instance-level firewall", "Subnet-level security", "Allow and deny rules".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!