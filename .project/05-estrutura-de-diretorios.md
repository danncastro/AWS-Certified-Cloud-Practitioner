# 🗺️ Estrutura do Repositório

Aqui está a arquitetura completa da sua aprovação, organizada para você escalar do zero absoluto ao nível de Arquiteto. 

```markdown
.
├── 00-estrategias-de-guerra/
│   ├── 00-panorama-real-clf-c02.md
│   ├── 01-tecnicas-de-leitura-de-questoes.md
│   ├── 02-metodo-de-eliminacao-de-alternativas.md
│   └── 03-caderno-de-erros-recorrentes.md
│   └── 04-gatilhos-visuais-pt-en.md
│   └── 05-plano-de-acao-30-dias.md
├── 01-fundamentos-e-infraestrutura-global/
│   ├── 00-o-que-e-cloud-computing.md
│   ├── 01-beneficios-agilidade-economia-escala.md
│   ├── 02-infraestrutura-global-regioes-e-azs.md
│   ├── 03-edge-locations-e-cloudfront-cache.md
│   ├── 04-modelo-responsabilidade-compartilhada-da-nuvem.md
│   ├── 05-detalhamento-iaas-paas-saas-na-pratica.md
│   ├── 06-tabela-comparativa-capex-vs-opex.md
│   ├── 07-modelos-de-implantacao-e-framework-aws.md
│   ├── 08-mnemonicos-fundamentos.md
│   ├── 09-lab-explorando-infraestrutura-global.md
│   └── 10-micro-simulado-fundamentos.md
├── 02-seguranca-identidade-e-conformidade/
│   ├── 00-iam-usuarios-grupos-e-policies.md
│   ├── 01-iam-roles-e-acesso-temporario.md
│   ├── 02-autenticacao-mfa-e-conta-root.md
│   ├── 03-protecao-contra-ddos-shield-e-waf.md
│   ├── 04-criptografia-kms-vs-cloudhsm-golden-rule.md
│   ├── 05-gestao-de-segredos-secrets-manager-vs-parameter-store.md
│   ├── 06-auditoria-e-logs-cloudtrail-quem-fez-o-que.md
│   ├── 07-deteccao-de-ameacas-guardduty-ml-vs-inspector-vuln.md
│   ├── 08-privacidade-de-dados-amazon-macie-pii.md
│   ├── 09-conformidade-e-relatorios-aws-artifact.md
│   ├── 10-central-de-seguranca-security-hub.md
│   ├── 11-tabela-iam-user-vs-group-vs-role.md
│   ├── 12-mnemonico-watch-trail-config.md
│   ├── 13-lab-configurando-politicas-iam-e-mfa.md
│   └── 14-micro-simulado-seguranca.md
├── 03-computacao-e-containers/
│   ├── 00-ec2-instancias-virtuais.md
│   ├── 01-opcoes-de-compra-regra-de-ouro-spot.md
│   ├── 02-auto-scaling-e-elastic-load-balancing.md
│   ├── 03-lambda-processamento-serverless-event-driven.md
│   ├── 04-containers-ecs-fargate-e-eks-kubernetes.md
│   ├── 05-outras-opcoes-lightsail-e-batch.md
│   ├── 06-tabela-comparativa-familias-instancia-ec2.md
│   ├── 07-mnemonicos-computacao.md
│   ├── 08-lab-lancando-instancia-ec2-com-userdata.md
│   └── 09-micro-simulado-computacao.md
├── 04-armazenamento-e-transferencia/
│   ├── 00-s3-armazenamento-de-objetos-api.md
│   ├── 01-s3-classes-de-armazenamento-e-ciclo-vida.md
│   ├── 02-ebs-volumes-em-bloco-disco-virtual.md
│   ├── 03-efs-sistema-arquivos-compartilhado-nfs.md
│   ├── 04-arquivamento-glacier-flexible-vs-deep-archive.md
│   ├── 05-migracao-fisica-familia-snow-offline.md
│   ├── 06-nuvem-hibrida-storage-gateway.md
│   ├── 07-tabela-objeto-s3-bloco-ebs-arquivo-efs.md
│   ├── 08-mnemonicos-armazenamento.md
│   ├── 09-lab-hospedagem-site-estatico-s3.md
│   └── 10-micro-simulado-armazenamento.md
├── 05-bancos-de-dados-e-analytics/
│   ├── 00-rds-banco-relacional-gerenciado-sql.md
│   ├── 01-aurora-performance-e-resiliencia-nativa.md
│   ├── 02-dynamodb-nosql-chave-valor-escala.md
│   ├── 03-redshift-data-warehousing-analytics.md
│   ├── 04-athena-consultas-sql-no-s3-serverless.md
│   ├── 05-cache-em-memoria-elasticache-redis.md
│   ├── 06-processamento-big-data-emr-hadoop.md
│   ├── 07-visualizacao-de-dados-quicksight.md
│   ├── 08-tabela-rds-vs-dynamodb-relacional-vs-nosql.md
│   ├── 09-mnemonicos-bancos-de-dados.md
│   ├── 10-lab-criando-banco-rds-multi-az.md
│   └── 11-micro-simulado-bancos-de-dados.md
├── 06-redes-e-conectividade/
│   ├── 00-vpc-rede-privada-virtual-isolada.md
│   ├── 01-subnets-publicas-vs-privadas.md
│   ├── 02-gateways-internet-igw-e-nat-gateway.md
│   ├── 03-security-groups-stateful-vs-nacls-stateless.md
│   ├── 04-conectividade-hibrida-vpn-vs-direct-connect.md
│   ├── 05-route-53-dns-global-e-politicas-roteamento.md
│   ├── 06-vpc-peering-e-endpoints-gateway-vs-interface.md
│   ├── 07-transit-gateway-hub-central-de-redes.md
│   ├── 08-mnemonicos-redes.md
│   ├── 09-lab-arquitetando-vpc-com-acesso-internet.md
│   └── 10-micro-simulado-redes.md
├── 07-inteligencia-artificial-e-inovacao/
│   ├── 00-ia-generativa-llm-e-foundation-models.md
│   ├── 01-amazon-bedrock-e-amazon-q-assistentes.md
│   ├── 02-rag-vs-fine-tuning-grounding-contextual.md
│   ├── 03-sagemaker-ciclo-de-vida-ml-completo.md
│   ├── 04-servicos-ia-prontos-rekognition-polly.md
│   ├── 05-nlp-comprehend-e-textract-documentos.md
│   ├── 06-tabela-servicos-ia-por-caso-uso.md
│   ├── 07-mnemonicos-inovacao.md
│   └── 08-micro-simulado-ia-e-inovacao.md
├── 08-arquitetura-e-adocao-aws-caf/
│   ├── 00-well-architected-framework-6-pilares-detalhados.md
│   ├── 01-as-6-perspectivas-do-aws-caf-negocio-e-tecnica.md
│   ├── 02-estrategias-de-migracao-7-rs-rehost-replatform-refactor.md
│   ├── 03-alta-disponibilidade-az-vs-disaster-recovery-region.md
│   ├── 04-julgamento-arquitetural-menor-esforco-vs-custo.md
│   ├── 05-mnemonicos-arquitetura.md
│   └── 06-micro-simulado-arquitetura.md
├── 09-gestao-de-custos-e-governanca/
│   ├── 00-aws-organizations-e-faturamento-consolidado.md
│   ├── 01-control-tower-e-landing-zone-multi-conta.md
│   ├── 02-politicas-de-controle-de-servico-scp-guardrails.md
│   ├── 03-ferramentas-estimativa-pricing-calculator-pre-deploy.md
│   ├── 04-controle-e-alerta-aws-budgets-limites.md
│   ├── 05-analise-de-gastos-cost-explorer-historico.md
│   ├── 06-otimizacao-trusted-advisor-checks.md
│   ├── 07-planos-de-suporte-developer-business-enterprise-tam.md
│   ├── 08-tabela-planos-de-suporte-sla-e-concierge.md
│   ├── 09-mnemonicos-custos.md
│   └── 10-micro-simulado-custos.md
├── 10-preparacao-final/
│   ├── 00-cronograma-acelerado-30-dias.md
│   ├── 01-glossario-essencial-pt-en-visual.md
│   ├── 02-simulado-completo-v1-blueprint-real.md
│   ├── 03-simulado-completo-v2-blueprint-real.md
│   └── 04-checklist-final-de-done-aprovacao.md
└── assets/
    └── images/
```