# ESCOPO DO PROJETO, PADRÕES TÉCNICOS E RESTRIÇÕES

## 1. ESCOPO E OBJETIVOS MACRO
- [REQ-01.1] **Certificação Alvo:** O objetivo principal deste repositório é consolidar a documentação completa para a preparação da certificação **AWS Certified Cloud Practitioner (CLF-C02)**.
- [REQ-01.2] **Casamento de Fontes:** O modelo deve cruzar as informações densas dos arquivos de origem (incluindo as dicas avançadas de Solutions Architect e AI Practitioner) para enriquecer o guia da CLF-C02, mantendo o foco no escopo do exame Practitioner, mas trazendo profundidade onde as fontes exigirem.

## 2. ESTRUTURA DE ARQUIVOS E DIRETÓRIOS
- [REQ-PAD-02.1] **Padrão de Case:** Todos os diretórios e arquivos markdown (`.md`) devem seguir estritamente o padrão **kebab-case numerado** (letras minúsculas, separados por hífen).
- [REQ-PAD-02.2] **Modularização Extrema (Micro-arquivos):** O conteúdo deve ser fatiado ao máximo. Cada arquivo markdown deve conter, no máximo, de **200 a 300 linhas** de texto para garantir uma leitura leve, direta e dinâmica.
- [REQ-PAD-02.3] **Proibição de Resumos por Limitação:** O limite de linhas serve exclusivamente para forçar a criação de **mais subdivisões e novos arquivos**, sendo terminantemente proibido omitir, resumir ou simplificar detalhes técnicos, comandos, laboratórios ou dicas das fontes.

## 3. COMPONENTES VISUAIS E DIAGRAMAS
- [REQ-PAD-03.1] **Links de Mídia:** Toda menção a suporte visual ou mapeamento de imagens deve apontar para o diretório local de assets na raiz do repositório. Padrão de caminho: `/assets/images/`.
- [REQ-PAD-03.2] **Diagramas Nativos (Mermaid):** Sempre que houver explicação de fluxos de rede, topologias, arquiteturas de segurança ou interações entre serviços AWS, é obrigatória a inclusão de diagramas em **Mermaid (` ```mermaid `)** diretamente nos arquivos markdown.

## 4. ENGENHARIA PEDAGÓGICA (DILUIÇÃO ORGÂNICA)
- [REQ-PAD-04.1] **Distribuição de Hacks:** É proibido isolar cheatsheets, mnemônicos, laboratórios ou tabelas comparativas em módulos excluídos apenas no topo ou no fim do repositório. Esses elementos de estudo ativo devem ser mapeados **dentro de seus respectivos módulos técnicos**, logo após a teoria.
- [REQ-PAD-04.2] **Mapeamento de Laboratórios e Simulados:** Cada domínio técnico deve encerrar sua lista de arquivos com seus laboratórios práticos específicos, glossários de gatilhos visuais (PT-EN), cadernos de erros comuns daquele assunto e micro-simulados dedicados.

## 5. RESTRIÇÕES ABSOLUTAS E ANTI-ALUCINAÇÃO
- [REQ-PAD-05.1] **Saída Limpa:** Proibido o uso de placeholders (ex: `[TODO]`, `...`). Todo mapeamento na árvore deve ser real, explícito e definitivo.
- [REQ-PAD-05.2] **Abafo de Citações:** Nenhuma citação automatizada do tipo `[1]` ou `[2]` deve aparecer dentro dos blocos de código gerados.