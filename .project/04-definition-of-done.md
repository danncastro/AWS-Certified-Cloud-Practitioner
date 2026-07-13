# DEFINITION OF DONE (DoD) - CRITÉRIOS DE ACEITAÇÃO

## 1. DIRETRIZ DE VALIDAÇÃO
- [REQ-DoD-01.1] **Critério de Rejeição:** Uma entrega de artefato só será considerada concluída se satisfizer 100% dos critérios listados neste documento.

## 2. CHECKLIST GERAL DE ACEITAÇÃO
- [ ] **[DoD-01] Limpeza de Código:** Livre de citações de rodapé do NotebookLM (ex: `[1]`).
- [ ] **[DoD-02] Encapsulamento:** Árvore estruturada estritamente dentro de blocos de código Markdown (````markdown ... ````).
- [ ] **[DoD-03] Idioma:** Conteúdo em português do Brasil, mantendo termos técnicos e nomes de serviços AWS em inglês.
- [ ] **[DoD-04] Tom de Voz:** Estilo "papo reto", focado em analogias práticas e comunidade tech.

## 3. CHECKLIST ESPECÍFICO - ETAPA 1
- [ ] **[DoD-E1.1] Formatação das Chaves Canário:** Todas as **18 chaves** foram listadas de forma limpa, uma por linha, utilizando estritamente uma lista de marcadores (`* base-X: KEY-WORDS=...`). Proibido texto corrido ou contínuo.
- [ ] **[DoD-E1.2] Arquitetura Fluida e Diluída:** A árvore não possui agrupamentos artificiais de hacks no topo. Tabelas comparativas, laboratórios práticos, mnemônicos e cheatsheets estão distribuídos organicamente como arquivos internos de cada módulo temático.
- [ ] **[DoD-E1.3] Exaustividade:** Sem uso de reticências (`...`) ou placeholders na árvore.
- [ ] **[DoD-E1.4] Condição de Parada:** O modelo parou imediatamente após fechar o bloco de código da árvore.