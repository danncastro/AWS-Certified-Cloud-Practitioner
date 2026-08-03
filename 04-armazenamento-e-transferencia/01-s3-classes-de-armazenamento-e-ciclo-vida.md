# S3: Classes de Armazenamento e Ciclo de Vida

O Amazon S3 não é apenas um "balde" onde você joga arquivos. O segredo para dominar esse serviço (e acertar as questões da CLF-C02) é entender que cada byte armazenado tem um custo, e esse custo depende principalmente de **com que frequência os dados são acessados** e **quão rápido eles precisam ser recuperados**.

Guardar um log de três anos na classe **S3 Standard** é como pagar diária de hotel cinco estrelas para guardar uma caixa de documentos no porão. Funciona, mas custa caro e não faz sentido.

---

## 1. Classes de Armazenamento (S3 Storage Classes)

O Amazon S3 oferece diversas classes de armazenamento para equilibrar **custo**, **durabilidade**, **disponibilidade** e **tempo de recuperação**.

> **Importante:** Todas as classes (exceto **S3 One Zone-IA**) armazenam os dados em **pelo menos três Availability Zones (AZs)** da mesma Região AWS.

---

### S3 Standard (General Purpose)

É a classe padrão do Amazon S3.

Características:

* Baixa latência.
* Alta taxa de transferência.
* Alta disponibilidade (99,99%).
* Durabilidade de **99.999999999% (11 noves)**.

Ideal para:

* Sites e aplicações web.
* Conteúdo acessado frequentemente.
* Aplicações móveis.
* Analytics em tempo real.

---

### S3 Intelligent-Tiering

É a classe ideal quando você **não conhece o padrão de acesso** aos dados.

O serviço monitora automaticamente a frequência de acesso aos objetos e move cada um entre camadas de armazenamento mais baratas conforme necessário.

Vantagens:

* Economia automática.
* Não exige análise manual dos padrões de acesso.
* Não possui taxa de recuperação para objetos movidos entre as camadas de acesso frequente e infrequente.

Ideal para:

* Dados com padrão de acesso imprevisível.
* Grandes volumes de arquivos cujo comportamento muda ao longo do tempo.

---

### S3 Standard-Infrequent Access (Standard-IA)

Projetado para arquivos acessados poucas vezes, mas que precisam estar disponíveis imediatamente quando solicitados.

Características:

* Armazenamento mais barato que o Standard.
* Recuperação em milissegundos.
* Cobrança de taxa por recuperação dos objetos.

Ideal para:

* Backups.
* Arquivos antigos.
* Recuperação de desastres.
* Dados acessados apenas ocasionalmente.

---

### S3 One Zone-Infrequent Access (One Zone-IA)

Possui características semelhantes ao Standard-IA, porém armazena os dados em **apenas uma Availability Zone**.

Vantagens:

* Menor custo de armazenamento.

Desvantagens:

* Menor resiliência.
* Se a AZ for perdida, os dados poderão ser perdidos.

Ideal para:

* Dados facilmente recriáveis.
* Backups secundários.
* Arquivos temporários.

---

### S3 Glacier Instant Retrieval

Classe de arquivamento para dados acessados muito raramente, mas que ainda precisam ser recuperados em **milissegundos**.

Ideal para:

* Arquivos médicos.
* Conteúdo multimídia antigo.
* Documentos arquivados que ainda podem ser solicitados rapidamente.

---

### S3 Glacier Flexible Retrieval

Antigo Amazon S3 Glacier.

Permite diferentes opções de recuperação:

* **Expedited** (minutos)
* **Standard** (horas)
* **Bulk** (várias horas)

Ideal para:

* Arquivamento de longo prazo.
* Backups corporativos.
* Dados acessados poucas vezes por ano.

---

### S3 Glacier Deep Archive

É a classe de armazenamento **mais barata do Amazon S3**.

Características:

* Recuperação entre **12 e 48 horas**.
* Voltada para retenção de longo prazo.

Ideal para:

* Arquivos legais.
* Dados fiscais.
* Compliance.
* Retenção de 7 a 10 anos ou mais.

---

## 2. S3 Lifecycle Management (Gerenciamento do Ciclo de Vida)

Você não precisa mover arquivos manualmente entre classes de armazenamento.

O **S3 Lifecycle Management** permite criar regras automáticas (**Lifecycle Configuration Rules**) baseadas na idade dos objetos.

Existem duas ações principais.

### Transition Actions

Movem automaticamente os objetos para classes mais baratas.

Exemplo:

~~~
S3 Standard
        ↓
S3 Standard-IA
        ↓
S3 Glacier Flexible Retrieval
        ↓
S3 Glacier Deep Archive
~~~

---

### Expiration Actions

Excluem automaticamente objetos após determinado período.

Exemplos:

* Apagar logs após 365 dias.
* Remover arquivos temporários após 30 dias.
* Excluir backups antigos automaticamente.

~~~mermaid
graph TD
    A[Upload: S3 Standard]
    A -->|30 dias| B[S3 Standard-IA]
    B -->|90 dias| C[S3 Glacier Flexible Retrieval]
    C -->|3 anos| D[Exclusão Automática]

    style D fill:#f96,stroke:#333
~~~

---

## 3. Guia de Decisão Rápida

| Se o requisito for... | A resposta correta é... | Motivo |
| :--- | :--- | :--- |
| Uso frequente e baixa latência | **S3 Standard** | Classe padrão para acesso constante. |
| Não conhece o padrão de acesso | **S3 Intelligent-Tiering** | Otimiza custos automaticamente. |
| Pouco acesso, mas recuperação imediata | **S3 Standard-IA** | Storage barato com acesso em milissegundos. |
| Dados recriáveis | **S3 One Zone-IA** | Menor custo aceitando menor resiliência. |
| Arquivamento com recuperação imediata | **S3 Glacier Instant Retrieval** | Arquivo frio com acesso em milissegundos. |
| Arquivamento de longo prazo | **S3 Glacier Flexible Retrieval** | Recuperação em minutos ou horas. |
| Menor custo possível | **S3 Glacier Deep Archive** | Recuperação lenta, custo mínimo. |

---

## 4. Quando usar cada classe?

| Classe | Frequência de acesso | Tempo de recuperação | Custo |
| :--- | :--- | :--- | :--- |
| Standard | Frequente | Milissegundos | Alto |
| Intelligent-Tiering | Variável | Milissegundos | Variável |
| Standard-IA | Pouco frequente | Milissegundos | Médio |
| One Zone-IA | Pouco frequente | Milissegundos | Baixo |
| Glacier Instant Retrieval | Muito raro | Milissegundos | Muito baixo |
| Glacier Flexible Retrieval | Muito raro | Minutos a horas | Muito baixo |
| Glacier Deep Archive | Quase nunca | 12–48 horas | Mínimo |

---

## 🎯 Gatilho de Exame

Se aparecerem estes termos, pense imediatamente nestas associações:

* **S3 Storage Classes:** Diferentes níveis de custo e desempenho.
* **S3 Intelligent-Tiering:** Economia automática para padrões de acesso desconhecidos.
* **Unknown access patterns:** Intelligent-Tiering.
* **Standard-IA:** Pouco acesso, recuperação imediata.
* **One Zone-IA:** Dados recriáveis em apenas uma AZ.
* **Archive / Long-term retention:** Glacier.
* **Immediate retrieval:** Glacier Instant Retrieval.
* **Minutes to hours retrieval:** Glacier Flexible Retrieval.
* **12-48 hours retrieval:** Glacier Deep Archive.
* **Lifecycle Configuration Rules:** Automação do ciclo de vida dos objetos.
* **Transition Actions:** Mudança automática entre classes.
* **Expiration Actions:** Exclusão automática de objetos.
* **Cost Optimization:** Objetivo principal das Storage Classes e Lifecycle.

> **Sinal de Alerta:** A prova costuma diferenciar **frequência de acesso** e **tempo de recuperação**. Se o dado é acessado raramente, mas precisa ser recuperado imediatamente, pense em **Standard-IA** ou **Glacier Instant Retrieval**. Se a recuperação pode esperar horas e o objetivo é pagar o menor valor possível, a resposta será **S3 Glacier Deep Archive**.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 4: Amazon S3 - Armazenamento de Objetos e API](00-s3-armazenamento-de-objetos-api.md)
* [➡️ Módulo 4: Amazon EBS - Volumes em Bloco e o Disco Virtual do EC2](02-ebs-volumes-em-bloco-disco-virtual.md)

---
---