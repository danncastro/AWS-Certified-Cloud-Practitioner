EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '01-fundamentos-e-infraestrutura-global/', arquivo '05-modelo-responsabilidade-compartilhada-da-nuvem.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código. Não use blocos de código com Mermaid.

Mano, papo reto: vamos para o quinto arquivo do Módulo 01! Quero que você gere o conteúdo completo sobre o pilar de segurança mais importante da prova para o arquivo:
👉 '01-fundamentos-e-infraestrutura-global/05-modelo-responsabilidade-compartilhada-da-nuvem.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Explique o conceito do Shared Responsibility Model (Modelo de Responsabilidade Compartilhada) e o mantra definitivo que separa as obrigações.
2. Detalhe a responsabilidade da AWS: Segurança DA Nuvem (Security OF the Cloud). Explique que ela protege a infraestrutura global (hardware, software, redes e facilidades físicas que rodam os serviços, como regiões, AZs e Edge Locations).
3. Detalhe a responsabilidade do Cliente: Segurança NA Nuvem (Security IN the Cloud). Explique que o cliente cuida do sistema operacional (patches em EC2), configuração de rede (Security Groups), criptografia de dados (at rest e in transit), IAM (senhas e acessos) e os próprios dados da aplicação.
4. CRIE UMA SEÇÃO EXCLUSIVA PARA CONTROLES COMPARTILHADOS (Shared Controls): Explique que existem responsabilidades que são DIVIDIDAS (onde ambos têm um papel). Detalhe obrigatoriamente os 3 exemplos da documentação oficial que caem na prova:
   - Patch Management (Gerenciamento de Patches): A AWS corrige a infraestrutura/RDS; o cliente corrige o SO das EC2.
   - Configuration Management (Gerenciamento de Configuração): A AWS configura os dispositivos dela; o cliente configura os serviços e recursos dele.
   - Awareness & Training (Treinamento/Conscientização): A AWS treina o time dela; o cliente treina seus próprios funcionários.
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Shared Responsibility Model", "Security OF the cloud (AWS)", "Security IN the cloud (Customer)", "Shared Controls", "Patch Management", "Configuration Management", "Awareness and Training".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!