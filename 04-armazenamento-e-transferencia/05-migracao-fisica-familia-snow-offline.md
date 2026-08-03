# Família AWS Snow: Migração Física e Offline

Mano, papo reto: normalmente a gente envia dados para a AWS pela internet. O problema é que existe um ponto em que isso simplesmente deixa de ser prático.

Imagine migrar dezenas ou centenas de terabytes usando um link corporativo comum. Mesmo com uma conexão dedicada, a transferência pode levar semanas ou meses.

É para esse cenário que existe a **Família AWS Snow**.

A ideia é simples:

1. A AWS envia um equipamento físico para sua empresa.
2. Você copia os dados para ele localmente.
3. Envia o equipamento de volta.
4. A AWS carrega tudo para os serviços de destino.

Em vez de mover os dados pela internet, você move os dados pela estrada.

---

## 1. O Problema que a Família Snow Resolve

A banca costuma criar cenários onde a transferência via rede é tecnicamente possível, mas operacionalmente inviável.

Por exemplo:

- Migrar 100 TB usando um link de 100 Mbps.
- Transferir anos de backups para a nuvem.
- Fechar um data center inteiro.
- Operar em locais sem conectividade confiável.

Nesses casos, a pergunta não é:

> "Consigo transferir?"

A pergunta é:

> "Consigo transferir em um prazo aceitável?"

Se a resposta for "vai levar semanas ou meses", provavelmente a Família Snow entra na conversa.

> **Dica de prova:** sempre que o enunciado enfatizar volume massivo de dados, conectividade limitada ou migração offline, pense imediatamente em AWS Snow.

---

## 2. Os Membros da Família Snow

Cada dispositivo foi criado para uma escala diferente de operação.

A pegadinha da prova normalmente está em identificar **o tamanho do problema**.

---

### A. AWS Snowcone

O **Snowcone** é o menor membro da família.

Ele foi criado para ambientes remotos, locais com pouco espaço físico ou cenários onde transportar um equipamento grande seria inviável.

**Principais características:**

- Aproximadamente **8 TB de armazenamento utilizável**.
- Pequeno o suficiente para caber em uma mochila.
- Pode operar em locais remotos ou com infraestrutura limitada.
- Suporta processamento local através de recursos de Edge Computing.

**Casos de uso comuns:**

- Embarcações em alto-mar.
- Operações de mineração.
- Ambientes militares ou de campo.
- Escritórios remotos sem conectividade adequada.

**Diferencial importante:**

Além do envio físico, o Snowcone pode transferir dados para a AWS através do **AWS DataSync**, algo que o torna mais flexível para cenários híbridos.

---

### B. AWS Snowball Edge

O **Snowball Edge** é o equipamento que mais aparece nas provas.

Ele foi criado para migrações grandes e processamento local de dados.

Visualmente, parece uma maleta robusta preparada para transporte seguro.

Existem duas versões principais:

#### Storage Optimized

Focada em capacidade de armazenamento.

**Quando usar:**

- Migração de grandes volumes de arquivos.
- Transferência de backups corporativos.
- Projetos envolvendo centenas de terabytes.

Capacidade aproximada:

- Até **80 TB de armazenamento utilizável** por dispositivo.

---

#### Compute Optimized

Focada em processamento local.

Além do armazenamento, oferece muito mais recursos computacionais.

**Quando usar:**

- Processamento de vídeo.
- Machine Learning na borda (Edge).
- Análise local de dados antes do envio para a AWS.

Possui:

- Mais CPU.
- Mais memória.
- Opções com GPU.

---

### Edge Computing na prática

Essa é uma característica que a prova gosta de cobrar.

O Snowball Edge consegue executar serviços AWS localmente, incluindo:

- Instâncias EC2.
- Funções AWS Lambda.

Isso significa que você pode:

1. Receber os dados.
2. Processá-los localmente.
3. Filtrar ou transformar as informações.
4. Enviar apenas o resultado para a AWS.

Tudo isso sem depender de internet.

---

### C. AWS Snowmobile

O Snowmobile existe para resolver problemas absurdamente grandes.

E quando eu digo grandes, estou falando de empresas migrando data centers inteiros.

O Snowmobile é literalmente um contêiner transportado por caminhão que funciona como uma plataforma de transferência de dados em escala extrema.

**Capacidade:**

- Até **100 PB (Petabytes)** por unidade.

**Quando usar:**

- Migração de data centers completos.
- Projetos na escala de múltiplos petabytes.
- Migrações de exabytes utilizando vários Snowmobiles.

**Segurança:**

- Rastreamento por GPS.
- Monitoramento contínuo.
- Proteção física avançada.
- Possibilidade de escolta durante o transporte.

> Essa é uma das respostas mais fáceis da CLF-C02. Se aparecer migração de dezenas de petabytes ou escala de exabytes, praticamente grita "Snowmobile".

---

## 3. Quando Usar Rede e Quando Usar Snow?

Uma forma rápida de pensar:

**Volume pequeno ou médio?**

- Internet.
- AWS DataSync.
- AWS Direct Connect.

**Volume gigantesco?**

- Família Snow.

Bata o olho na comparação:

| Critério | Transferência via Rede | Família AWS Snow |
| :--- | :--- | :--- |
| **Volume de Dados** | GBs até poucos TBs | Dezenas de TBs até Exabytes |
| **Internet Necessária** | Sim | Não |
| **Velocidade para Grandes Volumes** | Pode levar semanas ou meses | Normalmente mais rápida |
| **Locais Remotos** | Limitado pela conectividade | Excelente opção |
| **Edge Computing** | Não | Sim (Snowcone e Snowball Edge) |

---

## 4. Segurança e Gestão

Mover dados fisicamente pode parecer menos seguro, mas a AWS pensou nisso desde o início.

### Criptografia com AWS KMS

Todos os dados armazenados nos dispositivos Snow são criptografados automaticamente utilizando o **AWS Key Management Service (KMS)**.

Ou seja:

- Se alguém interceptar o equipamento.
- Se o dispositivo for roubado.
- Se houver tentativa de acesso indevido.

Os dados continuam protegidos.

---

### AWS OpsHub

O **AWS OpsHub** é uma ferramenta gráfica que simplifica a administração dos dispositivos Snow.

Com ela você consegue:

- Configurar o equipamento.
- Acompanhar transferências.
- Gerenciar armazenamento.
- Administrar workloads executados localmente.

Pense nele como o "painel de controle" do Snow.

---

### Limpeza Segura

Após a conclusão do processo, a AWS realiza a higienização completa dos dispositivos seguindo padrões rigorosos de segurança.

Isso garante que os dados de um cliente nunca fiquem disponíveis para o próximo.

---

## 🎯 Gatilho de Exame

Se aparecer qualquer um destes termos, pense na Família AWS Snow:

- **AWS Snow Family:** dispositivos físicos para migração de dados em larga escala.
- **Offline Data Transfer:** transferência sem depender da internet.
- **Physical Data Migration:** migração através de hardware físico.
- **Edge Computing:** processamento local próximo da origem dos dados.
- **AWS Snowcone:** portátil, aproximadamente 8 TB e voltado para ambientes remotos.
- **AWS Snowball Edge:** transferência em larga escala com capacidade de processamento local.
- **AWS Snowmobile:** migração em escala de petabytes e exabytes.

---

> **Sinal de Alerta:** A banca costuma tentar confundir Snowball Edge com Direct Connect. Se o problema for apenas velocidade de rede, o Direct Connect pode resolver. Mas se o enunciado destacar **centenas de terabytes, petabytes, locais remotos ou migração offline**, a resposta geralmente está na Família AWS Snow.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 4: Arquivamento - Glacier Flexible Retrieval vs. Deep Archive](04-arquivamento-glacier-flexible-vs-deep-archive.md)
* [➡️ Módulo 4: AWS Storage Gateway - A Ponte para a Nuvem Híbrida](06-nuvem-hibrida-storage-gateway.md)

---
---
