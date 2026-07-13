# MANUAL DE ESTILO E DIRETRIZES DE ESCRITA

## 1. TOM DE VOZ E IDENTIDADE
- [REQ-ESC-01.1] **Papo Reto de Dev para Dev:** A comunicação deve ser clara, informal, direta e com atitude de comunidade de tecnologia. O texto deve parecer escrito por um desenvolvedor experiente explicando a infraestrutura para outro.
- [REQ-ESC-01.2] **Proibição de Termos Corporativos/Robóticos:** É terminantemente proibido o uso de jargões corporativos prolixos e artificiais comuns em IA. 
  - *Termos estritamente banidos:* "curadoria especializada", "hub centralizado", "sinergia de recursos", "ecossistema robusto", "abordagem holística", "universo AWS".
- [REQ-ESC-01.3] **Fluidez e Objetividade:** Elimine introduções longas, transições maçantes ou conclusões óbvias (ex: "Em suma...", "Portanto, como vimos..."). Vá direto ao ponto técnico.

## 2. DIDÁTICA E CONSTRUÇÃO PEDAGÓGICA
- [REQ-ESC-02.1] **Analogias com o Mundo Real:** Conceitos complexos de infraestrutura de nuvem devem ser explicados utilizando analogias com o dia a dia do desenvolvimento de software ou situações práticas do mundo real.
- [REQ-ESC-02.2] **Unificação de Teoria e Resumos:** Dados comparativos, tabelas de resumo e dicas rápidas de exame têm exatamente a mesma importância que o aprofundamento técnico. Eles devem ser integrados organicamente no corpo do arquivo de cada serviço, e não isolados ao final como meros apêndices.
- [REQ-ESC-02.3] **Foco Técnico Prático:** Sempre que um serviço for explicado, deve ficar evidente:
  - O que ele resolve na prática.
  - Quando usá-lo (Cenários de Uso).
  - Comandos, parâmetros ou nuances essenciais descritos nas fontes.

## 3. FOCO EM EXAME (MINDSET DE PROVA)
- [REQ-ESC-03.1] **Mnemônicos e Palavras-Chave:** Devem ser destacados mnemônicos, gatilhos mentais e as "palavras-chave da AWS" que as questões costumam cobrar (ex: se a questão fala em *armazenamento durável, barato e infrequente*, o gatilho visual deve apontar para as classes corretas do *Amazon S3*).
- [REQ-ESC-03.2] **Sinalização de Pegadinhas:** É mandatório criar blocos de destaque (usando blockquotes `>`) sinalizando pegadinhas recorrentes em simulados ou distinções cruciais entre serviços parecidos (ex: *Application Load Balancer* vs. *Network Load Balancer*).