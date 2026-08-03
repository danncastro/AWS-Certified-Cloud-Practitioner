# Mnemônicos e Atalhos: O Guia de Sobrevivência em Armazenamento

A parte de armazenamento da AWS costuma assustar no começo porque existem muitos serviços, classes e nomes parecidos. A boa notícia é que a prova da **CLF-C02** não quer que você decore tudo; ela quer saber se você consegue escolher **o serviço certo para o cenário certo**.

Este capítulo reúne os atalhos mentais que ajudam a eliminar alternativas rapidamente e acertar as questões sem precisar decorar dezenas de detalhes.

---

# 1. Mnemônicos de Ouro

## Amazon S3 e as Classes de Armazenamento

Pense no S3 como um armário onde você escolhe a "prateleira" conforme a frequência de acesso.

### Amazon S3 Standard

**"Sempre pronto."**

- Arquivos acessados com frequência.
- Baixa latência.
- Alta disponibilidade.
- Não existe tempo de espera para recuperar os dados.

**Lembre:** uso diário = Standard.

---

### Amazon S3 Intelligent-Tiering

**"Piloto automático."**

Ideal quando você **não sabe** com que frequência os arquivos serão acessados.

A AWS monitora o padrão de acesso e move automaticamente os objetos entre camadas para reduzir custos.

**Mnemônico:**

> Não sabe como o arquivo será usado?
>
> Deixe a AWS decidir.

---

### S3 Glacier Flexible Retrieval

**"Geladeira."**

O arquivo continua acessível, mas você precisa esperar um pouco para recuperá-lo.

Características:

- recuperação em minutos ou horas;
- retenção mínima de **90 dias**;
- excelente para backups antigos.

**Pense:**

> Está guardado, mas ainda pode ser necessário.

---

### S3 Glacier Deep Archive

**"Cofre congelado."**

É a opção de armazenamento mais barata da AWS.

Em compensação:

- recuperação leva **12 a 48 horas**;
- retenção mínima de **180 dias**.

Ideal para:

- auditorias;
- retenção legal;
- backups históricos.

**Pense:**

> Espero nunca precisar abrir esse arquivo.

---

## Amazon EBS

**"HD da EC2."**

Sempre que pensar em:

- disco;
- sistema operacional;
- banco de dados;
- boot da máquina;

...a resposta normalmente será **Amazon EBS**.

### Mnemônico

**EBS = Exclusivo**

O volume normalmente pertence a **uma instância** e existe dentro de **uma única Availability Zone**.

> A palavra **AZ Locked** quase sempre aponta para Amazon EBS.

---

## Amazon EFS

**"Drive de rede."**

Sempre que vários servidores precisarem enxergar os mesmos arquivos, pense em EFS.

Casos clássicos:

- WordPress compartilhando uploads;
- diretórios Home;
- aplicações distribuídas;
- clusters Linux.

### Mnemônico

**EFS = Família**

Todo mundo compartilha os mesmos arquivos.

Além disso:

- utiliza **NFS**;
- é **Regional**;
- funciona entre múltiplas Availability Zones.

---

## Família AWS Snow

Aqui o tamanho do dispositivo praticamente entrega a resposta.

### Snowcone

**"Cone."**

- pequeno;
- portátil;
- cerca de 8 TB;
- cabe literalmente em uma mochila.

Ideal para:

- locais remotos;
- ambientes sem infraestrutura;
- Edge Computing.

---

### Snowball Edge

**"Maleta."**

É o modelo mais comum nas provas.

Ideal para:

- dezenas ou centenas de TB;
- migração de petabytes utilizando vários dispositivos;
- processamento local com EC2 e Lambda.

---

### Snowmobile

**"Caminhão."**

Quando a questão falar em:

- dezenas de petabytes;
- exabytes;
- migração de um data center inteiro;

...o Snowmobile passa a fazer sentido.

---

## AWS Storage Gateway

**"Ponte."**

Ele conecta o ambiente **on-premises** à AWS.

O detalhe mais importante é o cache local.

Para a aplicação:

- parece que os arquivos continuam no servidor local.

Na prática:

- eles estão sendo sincronizados com a AWS.

---

# 2. Pegadinhas Favoritas da Prova

A banca costuma montar cenários muito parecidos para confundir quem decorou apenas os nomes dos serviços.

---

## Pegadinha 1 — Compartilhar um EBS entre várias EC2

❌ Errado.

O EBS não foi criado para servir como um compartilhamento de arquivos entre diversas instâncias.

Se o cenário falar em:

- cluster;
- várias EC2;
- mesma pasta;
- compartilhamento simultâneo;

a resposta normalmente será:

✅ **Amazon EFS**

> Essa é uma das pegadinhas favoritas da CLF-C02.

---

## Pegadinha 2 — Instalar Windows ou Linux no S3

❌ Errado.

O S3 não funciona como um disco do sistema operacional.

Ele é acessado via API.

Para instalar um sistema operacional ou armazenar bancos de dados:

✅ **Amazon EBS**

---

## Pegadinha 3 — Glacier mais barato

A questão pode mostrar várias classes Glacier.

Faça esta pergunta:

**O acesso precisa ser imediato?**

Se sim:

✅ Glacier Instant Retrieval

Se pode esperar horas:

✅ Glacier Deep Archive

---

## Pegadinha 4 — Snowball ou Snowmobile?

Muita gente pensa:

"Quanto maior o volume, Snowmobile."

Nem sempre.

Como regra prática para a prova:

- dezenas ou centenas de TB → Snowball Edge;
- alguns petabytes → normalmente vários Snowball Edge;
- dezenas de petabytes ou exabytes → Snowmobile.

---

## Pegadinha 5 — EFS para Windows

O Amazon EFS utiliza **NFS** e foi projetado para ambientes Linux.

Se a questão pedir um compartilhamento de arquivos **nativo para Windows (SMB)**, normalmente o serviço esperado será o **Amazon FSx**.

---

# 3. Tabela de Decisão Rápida

| Se a questão falar em... | Resposta | Por quê? |
| :--- | :--- | :--- |
| Disco de boot da EC2 | **Amazon EBS** | Armazenamento em bloco para o sistema operacional. |
| Banco de dados | **Amazon EBS** | Baixa latência e acesso em bloco. |
| Compartilhar arquivos entre servidores Linux | **Amazon EFS** | Sistema de arquivos NFS compartilhado. |
| Backups, imagens, vídeos ou logs | **Amazon S3** | Object Storage altamente escalável. |
| Dados com padrão de acesso desconhecido | **S3 Intelligent-Tiering** | A AWS otimiza automaticamente os custos. |
| Arquivamento por muitos anos | **S3 Glacier Deep Archive** | Menor custo de armazenamento. |
| Migração física de centenas de TB | **AWS Snowball Edge** | Transferência offline de grandes volumes. |
| Substituir biblioteca de fitas | **Storage Gateway (Tape Gateway)** | Emula uma Virtual Tape Library (VTL). |
| Ambiente híbrido com cache local | **AWS Storage Gateway** | Integra servidores locais ao armazenamento da AWS. |

---

# 4. Resumo Mental de 30 Segundos

Se bater branco na prova, lembre desta sequência:

- **S3** → Objetos → API → Buckets.
- **EBS** → Disco → EC2 → Boot.
- **EFS** → Arquivos → NFS → Compartilhamento.
- **Snow** → Migração física.
- **Storage Gateway** → Ponte entre on-premises e AWS.

Só isso já elimina boa parte das alternativas erradas.

---

## 🎯 Gatilho de Exame

Faça estas associações automaticamente:

| Se aparecer... | Pense em... |
| :--- | :--- |
| **Object Storage** | Amazon S3 |
| **Block Storage** | Amazon EBS |
| **File Storage** | Amazon EFS |
| **Bucket** | Amazon S3 |
| **NFS** | Amazon EFS |
| **Boot Volume** | Amazon EBS |
| **Shared File System** | Amazon EFS |
| **AZ Locked** | Amazon EBS |
| **Regional File System** | Amazon EFS |
| **Global Bucket Name** | Amazon S3 |
| **Offline Data Transfer** | AWS Snow Family |
| **Hybrid Cloud Storage** | AWS Storage Gateway |
| **Virtual Tape Library (VTL)** | Tape Gateway |

> **🚨 Sinal de Alerta:** Não confunda **durabilidade** com **disponibilidade**. O Amazon S3 Standard oferece **11 noves de durabilidade (99,999999999%)** e foi projetado para permanecer disponível mesmo com a perda simultânea de múltiplas instalações dentro de uma Região. Já o **S3 One Zone-IA** armazena os dados em apenas **uma Availability Zone**: se essa AZ for perdida, os dados também serão. Por isso, utilize o One Zone-IA apenas para informações que possam ser recriadas facilmente.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 4: S3 vs. EBS vs. EFS - O Tira-Dúvidas de Armazenamento](07-tabela-objeto-s3-bloco-ebs-arquivo-efs.md)
* [➡️ Módulo 4: Lab - Hospedagem de Site Estático no Amazon S3](09-lab-hospedagem-site-estatico-s3.md)

---
---