EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '04-armazenamento-e-transferencia/', arquivo '05-migracao-fisica-familia-snow-offline.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código. 

Mano, papo reto: vamos para o sexto arquivo do Módulo 04! Quero que você gere o conteúdo completo focado na Família AWS Snow para migração física de dados para o arquivo:
👉 '04-armazenamento-e-transferencia/05-migracao-fisica-familia-snow-offline.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente o desafio clássico de migração de grandes volumes de dados para a nuvem quando a largura de banda da rede corporativa é insuficiente ou o tempo de transferência digital seria impraticável.
2. Apresente os três principais membros da **Família AWS Snow** cobrados na prova:
   - AWS Snowcone: O dispositivo menor, leve e portátil (cabe em uma mochila), ideal para ambientes de borda (edge computing) e migrações de pequeno porte (até alguns terabytes).
   - AWS Snowball (Snowball Edge): O dispositivo robusto e seguro em formato de maleta resistente a violações e impactos, usado para migrações de dezenas a centenas de terabytes, suportando inclusive computação local em instâncias EC2 e funções Lambda no próprio dispositivo.
   - AWS Snowmobile: Um caminhão de 45 pés protegido por contêineres de alta segurança, projetado para migrações massivas da ordem de exabytes de dados corporativos.
3. Crie um guia de decisão rápida para a prova: quando usar transferência via rede vs quando disparar um dispositivo físico da família Snow.
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "AWS Snow family", "AWS Snowcone", "AWS Snowball Edge", "AWS Snowmobile", "Physical data migration", "Offline data transfer", "Petabyte-scale migration".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!