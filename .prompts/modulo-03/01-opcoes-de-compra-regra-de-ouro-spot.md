EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '03-computacao-e-containers/', arquivo '01-opcoes-de-compra-regra-de-ouro-spot.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o segundo arquivo do Módulo 03! Quero que você gere o conteúdo completo focado em Opções de Compra do EC2 e a Regra de Ouro das Instâncias Spot para o arquivo:
👉 '03-computacao-e-containers/01-opcoes-de-compra-regra-de-ouro-spot.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Apresente as quatro principais opções de compra de instâncias Amazon EC2 cobradas no exame:
   - On-Demand Instances: Pagamento por segundo/hora sem compromisso de longo prazo, ideal para cargas de trabalho imprevisíveis ou testes de curto prazo.
   - Reserved Instances (RIs) e Savings Plans: Descontos significativos (até 72%) em troca de um compromisso de uso de 1 ou 3 anos (Ideal para workloads estáveis e previsíveis).
   - Spot Instances: Descontos massivos de até 90% utilizando capacidade ociosa de computação da AWS, com a grande ressalva de que a AWS pode interromper/reclamar a instância dando um aviso prévio de apenas 2 minutos.
   - Dedicated Hosts / Dedicated Instances: Hardware físico totalmente dedicado a um único cliente (atende a requisitos estritos de conformidade e licenciamento de software).
2. Detalhe profundamente a "Regra de Ouro das Instâncias Spot": Nunca utilize instâncias Spot para bancos de dados relacionais, aplicações monolíticas sem tolerância a falhas ou cargas críticas que não podem ser interrompidas. Use Spot exclusivamente para processamento em lote (Batch), computação científica, renderização, ambientes de teste/CI-CD e aplicações tolerantes a falhas (Fault-tolerant workloads).
3. Crie uma matriz comparativa rápida de decisão para a prova.
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "On-Demand instances", "Reserved Instances (RIs)", "Savings Plans", "Spot Instances", "Unused compute capacity", "Two-minute interruption warning", "Fault-tolerant workloads".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!