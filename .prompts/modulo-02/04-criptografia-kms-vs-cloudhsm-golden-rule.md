EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '02-seguranca-identidade-e-conformidade/', arquivo '04-criptografia-kms-vs-cloudhsm-golden-rule.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o quinto arquivo do Módulo 02! Quero que você gere o conteúdo completo sobre Criptografia e Gerenciamento de Chaves para o arquivo:
👉 '02-seguranca-identidade-e-conformidade/04-criptografia-kms-vs-cloudhsm-golden-rule.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Explique os conceitos fundamentais de criptografia na nuvem: Criptografia em Repouso (Encryption at Rest - dados salvos em disco/S3/EBS/RDS) e Criptografia em Trânsito (Encryption in Transit - dados trafegando na rede com TLS/SSL).
2. Apresente o AWS KMS (Key Management Service): Serviço totalmente gerenciado pela AWS, multi-tenant, altamente disponível e integrado nativamente com quase todos os serviços da AWS para criar e controlar chaves de criptografia (KMS Keys / CMKs).
3. Apresente o AWS CloudHSM: Módulo de segurança de hardware (Hardware Security Module) dedicado e exclusivo para o cliente dentro de uma VPC. Explique que ele é focado em requisitos estritos de conformidade regulatória (FIPS 140-2 Level 3) onde o cliente precisa de controle exclusivo das chaves físicas.
4. Estabeleça a "Regra de Ouro" (Golden Rule) de decisão para a prova:
   - Se o enunciado focar em simplicidade, gerenciamento automático e integração com serviços AWS -> A resposta é AWS KMS.
   - Se o enunciado mencionar hardware dedicado/exclusivo, controle total das chaves físicas, FIPS 140-2 Level 3 ou normas regulatórias corporativas rígidas -> A resposta é AWS CloudHSM.
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "AWS KMS (Key Management Service)", "AWS CloudHSM", "Encryption at rest", "Encryption in transit", "Dedicated hardware", "FIPS 140-2 Level 3 compliance", "Symmetric vs Asymmetric keys".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!