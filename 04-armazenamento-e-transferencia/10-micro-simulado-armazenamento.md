# Micro-Simulado: Armazenamento e Transferência

Armazenamento na AWS é um dos temas com maior volume de questões na CLF-C02. A banca não quer apenas que você saiba que o S3 guarda arquivos; ela quer que você saiba qual classe de armazenamento economiza mais dinheiro e qual tipo de disco (bloco, arquivo ou objeto) resolve um problema de arquitetura multi-AZ. 

Bora testar se você está pronto para não cair nas pegadinhas de storage.

---

## Questões

**1. Uma empresa armazena um grande volume de dados na nuvem, mas os padrões de acesso variam constantemente e são imprevisíveis. A equipe técnica precisa de uma solução que reduza os custos de armazenamento automaticamente, sem exigir intervenção manual ou gerar taxas de recuperação de dados.**

**Qual classe de armazenamento do Amazon S3 atende a esse requisito?**

- A) S3 Standard.
- B) S3 Standard-Infrequent Access (S3 Standard-IA).
- C) S3 Intelligent-Tiering.
- D) S3 Glacier Deep Archive.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C (S3 Intelligent-Tiering)**
>
> * **Por que é a certa:** O S3 Intelligent-Tiering monitora os padrões de acesso e move automaticamente os objetos entre camadas de acesso frequente e infrequente conforme o uso muda. Ele faz isso sem cobrar taxas de recuperação, sendo ideal para dados com comportamento imprevisível.
> * **A pegadinha:** O ponto-chave do enunciado é "padrões de acesso variam constantemente e são imprevisíveis" aliado a "sem taxas de recuperação".
>
> * **A) S3 Standard:** Projetado para acesso frequente, sem redução automática de custos para dados que esfriam.
> * **B) S3 Standard-IA:** Exige que você saiba antecipadamente que os dados são acessados com menor frequência e cobra taxas de recuperação por gigabyte.
> * **D) S3 Glacier Deep Archive:** Focado em arquivamento de longuíssimo prazo, com tempos de recuperação de horas, inadequado para dados dinâmicos.

</details>

---

**2. Um arquiteto de soluções precisa configurar um sistema de arquivos compartilhado que possa ser montado simultaneamente por centenas de instâncias Amazon EC2 rodando Linux em múltiplas Zonas de Disponibilidade (AZs).**

**Qual serviço atende a essa necessidade?**

- A) Amazon Elastic Block Store (Amazon EBS).
- B) Amazon Elastic File System (Amazon EFS).
- C) Amazon S3.
- D) EC2 Instance Store.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B (Amazon EFS)**
>
> * **Por que é a certa:** O Amazon EFS é um sistema de arquivos gerenciado baseado em NFS com escopo regional, permitindo o acesso simultâneo de milhares de instâncias EC2 distribuídas em várias AZs.
> * **A pegadinha:** A banca adora tentar te confundir com o EBS quando o assunto é disco ou compartilhamento.
>
> * **A) Amazon EBS:** Armazenamento em bloco vinculado a uma única AZ (AZ-locked), não permitindo compartilhamento multi-AZ nativo entre centenas de instâncias.
> * **C) Amazon S3:** Armazena dados como objetos via API HTTP/HTTPS, e não como um sistema de arquivos tradicional montável por um sistema operacional.
> * **D) EC2 Instance Store:** Disco físico temporário e efêmero acoplado diretamente ao hardware host da instância.

</details>

---

**3. Uma organização precisa migrar 60 Petabytes (PB) de dados de seu data center local para a AWS. A conexão de rede atual da empresa é limitada e a transferência online levaria anos para ser concluída.**

**Qual ferramenta da Família AWS Snow é a mais adequada para essa escala massiva?**

- A) AWS Snowcone.
- B) AWS Snowball Edge Storage Optimized.
- C) AWS Snowmobile.
- D) AWS DataSync.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: C (AWS Snowmobile)**
>
> * **Por que é a certa:** O AWS Snowmobile é um caminhão de transporte de dados dedicado a migrações em escala de Exabytes (suporta até 100 PB por veículo), ideal para volumes massivos onde redes tradicionais falham.
> * **A pegadinha:** O volume massivo de 60 PB descarta dispositivos de pequeno/médio porte e aponta direto para o caminhão.
>
> * **A) AWS Snowcone:** Dispositivo ultraleve voltado para ambientes de borda e cargas bem menores (cerca de 8 TB).
> * **B) Snowball Edge:** Trata petabytes, mas sua capacidade por dispositivo é de aproximadamente 80 TB, exigindo centenas de unidades para 60 PB.
> * **D) AWS DataSync:** Ferramenta de transferência online via rede, descartada pela lentidão da conexão atual.

</details>

---

**4. Uma empresa deseja substituir sua infraestrutura de fitas físicas local por uma solução baseada em nuvem. A nova arquitetura deve emular uma Virtual Tape Library (VTL) utilizando o protocolo iSCSI, sem exigir alterações nos softwares de backup existentes.**

**Qual serviço deve ser utilizado?**

- A) AWS Storage Gateway - S3 File Gateway.
- B) AWS Storage Gateway - Tape Gateway.
- C) Amazon S3 Glacier Deep Archive.
- D) AWS Snowball Edge.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B (AWS Storage Gateway - Tape Gateway)**
>
> * **Por que é a certa:** O Tape Gateway permite que ambientes locais utilizem fitas virtuais baseadas em nuvem, integrando-se via iSCSI com softwares de backup tradicionais que antes usavam fitas físicas.
> * **A pegadinha:** A menção a "Virtual Tape Library (VTL)" e "iSCSI" são os gatilhos exatos para o Tape Gateway.
>
> * **A) S3 File Gateway:** Expõe o Amazon S3 por meio de protocolos de arquivo padrão (NFS e SMB), e não VTL/iSCSI.
> * **C) S3 Glacier Deep Archive:** Classe de armazenamento no backend, mas não o serviço de gateway híbrido que emula a fita.
> * **D) AWS Snowball Edge:** Dispositivo físico para transporte offline pontual de dados.

</details>

---

**5. Ao tentar acessar um site estático recém-hospedado no Amazon S3, um usuário externo recebe um erro "403 Forbidden". Qual das seguintes ações é um requisito obrigatório para permitir o acesso público de leitura aos arquivos do site?**

- A) Criar uma IAM Role vinculada ao bucket do S3.
- B) Desativar as configurações de "Block Public Access" e aplicar uma S3 Bucket Policy válida.
- C) Habilitar o versionamento de objetos (S3 Versioning) no bucket.
- D) Associar o bucket do S3 a uma Edge Location do Amazon CloudFront.

<details>
<summary>🔑 <b>Revelar Resposta Correta e Comentários</b></summary>

> **Resposta Correta: B (Desativar Block Public Access e aplicar S3 Bucket Policy)**
>
> * **Por que é a certa:** Por padrão, o S3 bloqueia qualquer acesso público por segurança. Para expor um site estático, é necessário desativar o "Block Public Access" e adicionar uma política de bucket que conceda permissão de leitura (`s3:GetObject`) publicamente.
> * **A pegadinha:** Muita gente tenta resolver permissões públicas criando regras no IAM, esquecendo que o S3 possui travas de segurança próprias na camada de bucket.
>
> * **A) IAM Role:** Usada para conceder permissões temporárias a usuários ou serviços internos da AWS, não para acesso público anônimo.
> * **C) S3 Versioning:** Protege contra exclusões acidentais, mas não altera as regras de acesso público.
> * **D) Amazon CloudFront:** Melhora a distribuição global, mas ainda exige que o S3 permita a leitura de origem.

</details>

---

## 🎯 Gatilho de Exame

Mapeie esses cenários para responder rápido:

* **11 noves de durabilidade** ➔ **Amazon S3**
* **AZ Locked (Preso à AZ)** ➔ **Amazon EBS**
* **Escopo Regional / Acesso Multi-AZ (NFS)** ➔ **Amazon EFS**
* **Menor custo de armazenamento na AWS** ➔ **S3 Glacier Deep Archive**
* **Integração híbrida / Armazenamento local** ➔ **AWS Storage Gateway**
* **Escala de Exabytes / Caminhão** ➔ **AWS Snowmobile**
* **Protocolo NFS/SMB para o S3** ➔ **S3 File Gateway**
* **Emulação de fita / iSCSI** ➔ **Tape Gateway**

---

> **Sinal de Alerta:**  
> A banca adora confundir os protocolos do Amazon FSx e EFS. Lembre-se:
> 
> - **Compartilhamento Windows (SMB)** ➔ **Amazon FSx for Windows File Server**.
> - **Compartilhamento Linux (NFS)** ➔ **Amazon EFS**.
> - **Bloqueio de acesso público no S3** exige alterar o *Block Public Access* antes da *Bucket Policy*.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 4: Lab - Hospedagem de Site Estático no Amazon S3](09-lab-hospedagem-site-estatico-s3.md)
* [➡️ Módulo 5: Amazon RDS: Banco Relacional Gerenciado (SQL)](../05-bancos-de-dados-e-analytics/00-rds-banco-relacional-gerenciado-sql.md)

---
---