EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '04-armazenamento-e-transferencia/', arquivo '09-lab-hospedagem-site-estatico-s3.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código.

Mano, papo reto: vamos para o penúltimo arquivo do Módulo 04, o nosso Lab Prático de Armazenamento! Quero que você gere o conteúdo completo focado em passo a passo prático para o arquivo:
👉 '04-armazenamento-e-transferencia/09-lab-hospedagem-site-estatico-s3.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Monte um guia mão na massa estruturado e fácil de seguir para o estudante executar no AWS Free Tier / Console AWS.
2. Defina os objetivos do laboratório:
   - Criar um Amazon S3 Bucket com nome globalmente único.
   - Ajustar as configurações de **Block Public Access** para permitir o acesso público de leitura ao site.
   - Escrever e aplicar uma **Bucket Policy** baseada em JSON concedendo permissão de leitura pública (GetObject) para os objetos do site.
   - Habilitar o recurso de **Static Website Hosting** configurando os arquivos de índice (`index.html`) e de erro (`error.html`).
   - Fazer o upload de uma página HTML simples e testar o endpoint público gerado pela AWS.
3. Apresente os blocos de código JSON da Bucket Policy e do arquivo HTML de forma clara e explicada.
4. Adicione uma verificação de validação (copiar o endpoint do site estático, colar no navegador e confirmar que a página web carregou perfeitamente).
5. Garanta a seção "🎯 Gatilho de Exame" mapeando termos e ações em inglês como "S3 Static Website Hosting", "Block Public Access configuration", "S3 Bucket Policy JSON", "Public read permissions", "Website endpoint URL".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!