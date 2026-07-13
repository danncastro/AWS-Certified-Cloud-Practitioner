# PROTOCOLO DE EXECUÇÃO EM PIPELINE (WORKFLOW)

## 1. DIRETRIZ GERAL DE ITERAÇÃO
- [REQ-PIPE-01.1] **Execução Estritamente Faseada:** O projeto deve progredir de forma linear, uma etapa por vez. É terminantemente proibido que o modelo execute tarefas de etapas posteriores de forma antecipada sem a aprovação explícita do usuário no chat.
- [REQ-PIPE-01.2] **Ordens de Parada (Gatekeepers):** Ao final de cada etapa especificada neste documento, o modelo deve interromper a geração imediatamente e aguardar o comando de validação do usuário.

## 2. FASES DA PIPELINE DE PRODUÇÃO

### ETAPA 1: AUDITORIA DE LEITURA + ARQUITETURA DA ÁRVORE DE DIRETÓRIOS
- [REQ-PIPE-02.1] **Validação de Entrada (Checkpoint Canário):** Como pré-requisito obrigatório, o modelo deve escanear todas as fontes de dados do painel lateral de ponta a ponta, extraindo e listando as **18 chaves canário** ocultas.
- [REQ-PIPE-02.2] **Formato das Chaves:** As 18 chaves devem ser exibidas estritamente no topo da resposta, uma por linha, no formato: `"Arquivo X: KEY-WORDS=VALOR_ENCONTRADO"`.
- [REQ-PIPE-02.3] **Geração de Árvore Exaustiva:** Logo abaixo das chaves, o modelo deve gerar a árvore completíssima de pastas e arquivos markdown (`.md`) para o repositório, aplicando de forma irrestrita os padrões definidos em `01-padroes-e-restricoes.md`.
- [REQ-PIPE-02.4] **Mapeamento Orgânico:** Laboratórios práticos, simulados e tabelas comparativas extraídos de todas as fontes (incluindo as secundárias de AI e SAA) devem ser injetados nominalmente em seus respectivos módulos lógicos.
- [REQ-PIPE-02.5] **Condição de Parada 1:** O modelo deve entregar a listagem das 18 chaves, a árvore de diretórios dentro de um bloco de código markdown e PARAR imediatamente. Não deve redigir o README.md nem o conteúdo dos módulos ainda.

### ETAPA 2: ANÁLISE DE LACUNAS (GAP ANALYSIS)
- [REQ-PIPE-03.1] **Mapeamento de Escopo:** Após aprovação da Etapa 1, o modelo realizará o relatório de Gap Analysis, confrontando a árvore gerada com o Guia de Exame Oficial da AWS CLF-C02.
- [REQ-PIPE-03.2] **Condição de Parada 2:** O modelo deve entregar o relatório de gaps e PARAR, aguardando autorização.

### ETAPA 3: PRODUÇÃO SPRINTADA DE CONTEÚDO
- [REQ-PIPE-04.1] **Geração por Módulos:** O conteúdo técnico será redigido em lotes (sprints) solicitados individualmente pelo usuário (ex: "Gere o Módulo 01").