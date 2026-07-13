EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '01-fundamentos-e-infraestrutura-global/', arquivo '04-edge-locations-e-cloudfront-cache.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código. Não use blocos de código com Mermaid.

Mano, papo reto: vamos para o quarto arquivo do Módulo 01! Quero que você gere o conteúdo completo focado na rede de entrega de conteúdo da AWS para o arquivo:
👉 '01-fundamentos-e-infraestrutura-global/04-edge-locations-e-cloudfront-cache.md'

Diretrizes de Conteúdo para este arquivo:
1. Explique o conceito de Edge Location (Pontos de Presença): locais de data center menores espalhados pelo mundo (muito mais numerosos que as Regiões) que não rodam sua aplicação principal, mas servem para aproximar os dados do usuário final.
2. Apresente o Amazon CloudFront como a CDN (Content Delivery Network) global da AWS que usa essas Edge Locations para fazer cache de conteúdo estático (imagens, vídeos, HTML) e dinâmico, reduzindo a latência drasticamente.
3. Explique a diferença de fluxo: na primeira requisição, o CloudFront busca o dado na origem (S3 ou EC2) e guarda o cache na Edge Location. Nas próximas requisições, o usuário baixa o arquivo direto do ponto mais próximo, economizando banda e processamento da origem.
4. Faça um paralelo simples para o estudante entender que Edge Location não é Região nem AZ (não serve para subir bancos de dados ou instâncias EC2 tradicionais, serve para distribuição).
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos cruciais em inglês como "Edge Location", "Amazon CloudFront", "Content Delivery Network (CDN)", "Cache", "Low latency", "Reduce load on origin".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!