# Comparativo de Famílias EC2: Escolhendo a Instância Certa

A AWS possui centenas de tipos de instâncias EC2, mas a CLF-C02 não quer que você decore todas elas. O que a prova realmente cobra é se você consegue identificar qual família atende melhor cada tipo de carga de trabalho (**Workload Profiling**). A regra é simples: CPU para processamento, memória para bancos de dados, armazenamento para I/O intenso e GPU para aceleração.

---

## 1. Famílias de Instâncias EC2

Cada família foi criada para resolver um tipo específico de problema.

| Família | Categoria | Melhor para |
| :--- | :--- | :--- |
| **T e M** | **General Purpose** | Servidores web, aplicações gerais, microsserviços e ambientes de desenvolvimento. |
| **C** | **Compute Optimized** | Processamento intensivo, HPC, renderização, transcodificação e Batch Jobs. |
| **R, X e Z** | **Memory Optimized** | Bancos de dados, caches (Redis/Memcached) e aplicações que exigem muita RAM. |
| **I, D e H** | **Storage Optimized** | Bancos NoSQL, Data Warehouses e workloads com alto IOPS. |
| **P, G, Inf e Tr** | **Accelerated Computing** | Machine Learning, IA, GPUs, renderização gráfica e computação científica. |

---

## 2. Regra de Ouro da Prova

Se identificar estes cenários, a resposta costuma ser imediata:

* **Aplicação de uso geral:** Família **M** (ou **T** para cargas leves).
* **Muito processamento (CPU):** Família **C**.
* **Muito consumo de memória:** Família **R**.
* **Disco extremamente rápido:** Família **I**.
* **GPU ou Machine Learning:** Família **P** ou **G**.

> **Lembrete:** A série **T** é **Burstable**. Ela acumula **CPU Credits**, sendo ideal para aplicações que ficam grande parte do tempo ociosas, mas apresentam picos ocasionais de processamento.

---

## 3. Entendendo o Nome da Instância

Exemplo: `m5.2xlarge`

* **m** → Família da instância.
* **5** → Geração da instância (quanto mais nova, melhor custo-benefício).
* **2xlarge** → Tamanho da instância (CPU, memória e rede).

---

## 🎯 Gatilho de Exame

Se aparecerem estes termos, associe imediatamente:

* **General Purpose:** Equilíbrio entre CPU, memória e rede.
* **Compute Optimized:** Alto desempenho de CPU.
* **Memory Optimized:** Grande quantidade de memória RAM.
* **Storage Optimized:** Alto desempenho de armazenamento (IOPS).
* **Accelerated Computing:** GPU, IA, Machine Learning e computação científica.
* **Workload Profiling:** Escolher a família conforme a necessidade da aplicação.

> **Sinal de Alerta:** A banca costuma descrever o comportamento da aplicação, não a família da instância. Primeiro descubra qual é o recurso que está sendo mais exigido (CPU, memória, armazenamento ou GPU) e só depois escolha a família correspondente.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 3: Amazon Lightsail e AWS Batch - Simplicidade e Lote](05-outras-opcoes-lightsail-e-batch.md)
* [➡️ Módulo 3: Mnemônicos e Atalhos - O Guia de Sobrevivência em Computação](07-mnemonicos-computacao.md)

---
---