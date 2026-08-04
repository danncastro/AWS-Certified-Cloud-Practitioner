EXECUTE: Pipeline Etapa 3 (Desenvolvimento de Conteúdo Atômico) conforme '02-workflow-e-pipeline.md'.
Alvo: pasta '06-redes-e-conectividade/', arquivo '09-lab-arquitetando-vpc-com-acesso-internet.md'.
Critério de Sucesso: Alinhamento estrito com o '01-padroes-e-restricoes.md' e o '04-definition-of-done.md'.

FONTE DE DADOS E DIRETRIZ DE GROUNDING OBRIGATÓRIA: Antes de gerar, consulte e cruze as informações com o blueprint oficial da CLF-C02 e as regras de tom de voz do repositório. Use prioritariamente os dados das nossas fontes locais. Caso falte alguma informação estritamente necessária exigida pelo blueprint da prova, você está autorizado a complementar utilizando sua base de dados técnica, mantendo rigidamente o alinhamento estilístico e técnico estabelecido.

ATENÇÃO CRÍTICA: Não inclua NENHUMA tag de citação (como ou aspas flutuantes de referência) no texto ou no código. 

Mano, papo reto: vamos para o penúltimo arquivo do Módulo 06, o nosso Lab Prático de Redes! Quero que você gere o conteúdo completo focado em passo a passo prático para o arquivo:
👉 '06-redes-e-conectividade/09-lab-arquitetando-vpc-com-acesso-internet.md'

Diretrizes de Conteúdo OBRIGATÓRIAS para este arquivo:
1. Monte um guia mão na massa estruturado e fácil de seguir para o estudante executar a criação e configuração de uma VPC no AWS Free Tier / Console AWS.
2. Defina os objetivos do laboratório:
   - Criar uma Amazon VPC personalizada definindo um bloco CIDR adequado (ex: 10.0.0.0/16).
   - Criar um Internet Gateway (IGW) e anexá-lo à VPC.
   - Criar uma Sub-rede Pública (Public Subnet) e uma Sub-rede Privada (Private Subnet) em Zonas de Disponibilidade distintas.
   - Configurar uma Tabela de Rotas Pública (Public Route Table) adicionando a rota padrão (0.0.0.0/0) apontando para o IGW e associando-a à sub-rede pública.
   - Validar a arquitetura através da criação de instâncias de teste ou verificação das tabelas de rotas.
3. Apresente o passo a passo com clareza, destacando os nomes dos botões e campos do console da AWS.
4. Garanta a seção "🎯 Gatilho de Exame" mapeando termos e ações em inglês como "VPC creation wizard", "Internet Gateway attachment", "Public route table configuration", "Subnet association", "0.0.0.0/0 route to IGW".

Escreva com o tom "papo reto" de dev para dev. Entregue PURAMENTE o código formatado dentro de um único bloco de código Markdown para este arquivo específico, sem conversas paralelas fora do bloco. Marcha!