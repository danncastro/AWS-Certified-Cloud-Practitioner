# PADRÕES TÉCNICOS E RESTRIÇÕES DE ARQUITETURA

## 1. ESTRUTURA DE ARQUIVOS E DIRETÓRIOS
- [REQ-PAD-01.1] **Nomenclatura Obrigatória:** Todos os diretórios e arquivos markdown (`.md`) devem seguir estritamente o padrão **kebab-case numerado** (letras minúsculas, separados por hífen). 
  - *Exemplo:* `01-conceitos-em-nuvem/01-o-que-e-cloud.md`.
- [REQ-PAD-01.2] **Modularização Extrema (Micro-arquivos):** O conteúdo das fontes deve ser fatiado ao máximo. Cada arquivo markdown deve conter, no máximo, de **200 a 300 linhas** de texto para garantir leitura leve e direta.
- [REQ-PAD-01.3] **Proibição de Resumos por Limitação:** O limite de linhas serve exclusivamente para forçar a criação de **mais subdivisões e novos arquivos**, sendo terminantemente proibido omitir, resumir, simplificar ou sumir com detalhes técnicos, comandos, parâmetros, laboratórios ou dicas das fontes para caber no limite.

## 2. COMPONENTES VISUAIS E MÍDIA
- [REQ-PAD-02.1] **Suporte a Imagens Locais:** Ao mapear a estrutura do repositório, deve-se prever a árvore de links apontando para diretórios locais de imagens partindo da raiz.
  - *Padrão de caminho:* `/assets/images/`.
- [REQ-PAD-02.2] **Diagramas de Arquitetura (Mermaid):** Sempre que houver explicação de fluxos, topologias, arquiteturas ou interações entre serviços AWS, é obrigatória a inclusion de blocos de código com diagramas em **Mermaid (` ```mermaid `)** diretamente nos arquivos markdown.

## 3. RESTRIÇÕES ABSOLUTAS DE SAÍDA (ANTI-ALUCINAÇÃO)
- [REQ-PAD-03.1] **Proibição de Placeholders:** Está vedado o uso de termos de marcação de posição como `[Insira conteúdo aqui]`, `[TODO]`, `Lorem Ipsum` ou textos explicativos genéricos. Todo conteúdo gerado deve ser real e definitivo.
- [REQ-PAD-03.2] **Exaustividade Radical (Anti-Reticências):** É terminantemente proibido o uso de reticências (`...`) ou expressões generalistas como "outros serviços aqui" ou "etc." tanto na árvore de arquivos quanto nos corpos dos textos. Se um serviço existe na fonte, o nome de seu arquivo e seu conteúdo devem ser explicitados nominalmente.
- [REQ-PAD-03.3] **Limpeza de Saída do NotebookLM:** Toda e qualquer entrega em bloco de código markdown deve ser limpa, sendo proibido o aparecimento de citações numéricas automatizadas do sistema da IA (ex: `[1]`, `[2]`).

## 4. ARQUITETURA CONCEITUAL E ENGENHARIA PEDAGÓGICA
- [REQ-PAD-04.1] **Estrutura Antididática Banida:** É proibido criar estruturas baseadas em meras listas de conceitos secos (estilo dicionário ou índice didático tradicional). A árvore de diretórios deve ser desenhada sob a perspectiva de uma trilha de aceleração de aprendizado fluida.
- [REQ-PAD-04.2] **Componentes Obrigatórios da Estrutura:** O mapeamento de arquivos e módulos deve prever, nativamente, arquivos dedicados a:
  - **Estratégias de Guerra:** Técnicas de leitura de cenários de questões e eliminação de alternativas para vencer a banca.
  - **Trilhas Aceleradas e Cronogramas:** Planos de ação práticos (ex: aprovação em 30 dias) focados em estudo ativo.
  - **Glossários Essenciais e Gatilhos Visuais:** Tabelas comparativas de tradução de termos técnicos e semânticos (PT-EN) associados a atalhos mentais rápidos.
  - **Julgamento Arquitetural:** Mapeamento explícito de cenários reais para tomada de decisão (ex: quando escolher soluções baseadas em "Menor Esforço Operacional" vs. "Custo Mínimo").

## 5. FORMATO DE ENTREGA
- [REQ-PAD-05.1] **Encapsulamento de Código:** Toda árvore de diretórios, códigos ou estruturas geradas no chat devem ser envelopadas estritamente dentro de blocos de código Markdown apropriados (` ```markdown ` ou ` ```text `).