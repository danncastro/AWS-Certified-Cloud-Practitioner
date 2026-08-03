# Amazon EBS: Volumes em Bloco e o Disco Virtual do EC2

Se o Amazon S3 é o seu "Google Drive" na nuvem, o **Amazon EBS (Elastic Block Store)** é o seu SSD ou HD virtual. Ele é um serviço de **Block Storage** (armazenamento em blocos) de alta performance, projetado especificamente para ser utilizado com instâncias **Amazon EC2**.

Diferente do armazenamento temporário (**Instance Store**), os volumes EBS são **persistentes**. Isso significa que, se você parar ou reiniciar a instância, os dados continuam armazenados no volume.

---

## 1. O Escopo Geográfico: A "Prisão" da AZ

Este é um dos conceitos mais cobrados na prova: um volume EBS pertence a uma única **Availability Zone (AZ)**.

* **Escopo por AZ:** Um volume EBS é criado dentro de uma AZ específica e só pode ser anexado diretamente a instâncias EC2 que estejam nessa mesma AZ.
* **Alta Disponibilidade:** A AWS replica automaticamente os dados do volume dentro da própria Availability Zone para protegê-los contra falhas de hardware.
* **Migração entre AZs:** Não é possível mover um volume diretamente para outra AZ. O procedimento correto é criar um **Snapshot** e restaurá-lo como um novo volume na AZ desejada.

> **Importante:** O EBS é um recurso **regional**, mas cada volume individual existe em apenas uma Availability Zone.

---

## 2. Famílias de Volumes: SSD vs. HDD

A escolha do volume depende do tipo de carga de trabalho.

De forma geral:

* **SSD:** Prioriza baixa latência e alto número de IOPS.
* **HDD:** Prioriza alto throughput para grandes volumes de dados sequenciais.

---

### SSD-backed (Baixa Latência e Alto IOPS)

Indicados para aplicações transacionais.

#### General Purpose SSD (gp3 / gp2)

É a opção recomendada para a maioria dos workloads.

Características:

* Excelente equilíbrio entre custo e desempenho.
* Ideal para volumes de boot.
* Indicado para bancos de dados pequenos e médios.
* O **gp3** permite configurar IOPS e throughput independentemente da capacidade do volume.

É a escolha padrão na maioria dos cenários.

---

#### Provisioned IOPS SSD (io1 / io2)

Projetado para aplicações extremamente sensíveis à latência.

Ideal para:

* Bancos de dados críticos.
* Sistemas ERP.
* Grandes workloads transacionais.

Sua principal característica é oferecer **IOPS previsíveis e garantidos**.

---

### HDD-backed (Alto Throughput)

Indicados para acesso sequencial de grandes arquivos.

#### Throughput Optimized HDD (st1)

Ideal para:

* Big Data.
* Data Warehouses.
* Processamento de logs.
* Streaming de grandes volumes de dados.

---

#### Cold HDD (sc1)

É a opção mais econômica entre os volumes EBS.

Ideal para:

* Arquivos pouco acessados.
* Dados frios.
* Armazenamento de baixo custo.

> **Regra de Ouro:** Volumes HDD (**st1** e **sc1**) **não podem ser utilizados como volume de boot** de uma instância EC2.

---

## 3. Amazon EBS Snapshots

Os **Snapshots** são backups **Point-in-Time** dos volumes EBS.

Eles permitem:

* Restaurar dados.
* Criar novos volumes.
* Migrar volumes entre Availability Zones.
* Copiar volumes para outras Regiões AWS.

### Snapshots Incrementais

Após o primeiro Snapshot completo, os próximos armazenam apenas os blocos modificados.

Isso reduz:

* Tempo de backup.
* Espaço utilizado.
* Custo de armazenamento.

### Armazenamento

Embora sejam gerenciados pelo Amazon EBS, os Snapshots são armazenados automaticamente no **Amazon S3**, oferecendo alta durabilidade.

~~~mermaid
graph LR

A[Volume EBS] --> B[Snapshot]

B --> C[(Amazon S3)]

C --> D[Novo Volume EBS]

D --> E[Outra AZ ou Região]
~~~

---

## 4. Delete on Termination

Todo volume EBS possui um atributo chamado **Delete on Termination**.

Ele define o comportamento do volume quando a instância EC2 é encerrada (**Terminate**).

* **Habilitado (padrão para o volume raiz):** O volume é excluído junto com a instância.
* **Desabilitado:** O volume permanece disponível mesmo após a exclusão da instância.

Esse recurso é bastante utilizado quando se deseja preservar dados importantes.

---

## 5. Guia de Decisão Rápida

| Se o requisito for... | A resposta correta é... | Motivo |
| :--- | :--- | :--- |
| Disco para sistema operacional | **gp3** | Melhor equilíbrio entre custo e desempenho. |
| Banco de dados crítico | **io2** | IOPS garantidos e baixa latência. |
| Big Data ou processamento sequencial | **st1** | Alto throughput. |
| Dados frios e pouco acessados | **sc1** | Menor custo entre os volumes EBS. |
| Backup de um volume | **EBS Snapshot** | Backup Point-in-Time armazenado no S3. |
| Migrar volume entre AZs | **Snapshot + Restore** | Não existe movimentação direta entre AZs. |

---

## 🎯 Gatilho de Exame

Se aparecerem estes termos, pense imediatamente em **Amazon EBS**:

* **Amazon EBS:** Block Storage para instâncias EC2.
* **Block Storage:** Armazenamento em blocos para sistemas operacionais e aplicações.
* **Availability Zone Scope:** Cada volume pertence a apenas uma AZ.
* **Persistent Storage:** Os dados permanecem após parar ou reiniciar a instância.
* **General Purpose SSD (gp3):** Melhor custo-benefício para uso geral.
* **Provisioned IOPS (io1/io2):** Alto desempenho para bancos de dados críticos.
* **Throughput Optimized HDD (st1):** Alto throughput para grandes arquivos.
* **Cold HDD (sc1):** Armazenamento de baixo custo para dados frios.
* **EBS Snapshots:** Backups Point-in-Time armazenados no Amazon S3.
* **Incremental Backups:** Apenas os blocos alterados são armazenados.
* **Delete on Termination:** Define se o volume será removido quando a instância for encerrada.

> **Sinal de Alerta:** O Amazon EBS foi projetado para ser utilizado com **uma única instância EC2 por vez** (com exceções específicas fora do escopo da CLF-C02). Se a questão pedir um sistema de arquivos compartilhado entre diversas instâncias Linux simultaneamente, a resposta correta é o **Amazon EFS**, e não o EBS.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 4: S3 - Classes de Armazenamento e Ciclo de Vida](01-s3-classes-de-armazenamento-e-ciclo-vida.md)
* [➡️ Módulo 4: Amazon EFS - Arquivos Compartilhados e a Magia do NFS](03-efs-sistema-arquivos-compartilhado-nfs.md)

---
---