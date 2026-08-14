# Lab: Alta Disponibilidade com RDS Multi-AZ

Em produção, deixar um banco de dados crítico em uma única Zona de Disponibilidade (AZ) é colocar um ponto único de falha no caminho da aplicação.

Pode funcionar perfeitamente por meses. Mas, se aquela AZ tiver uma falha séria, o banco vai junto.

O **Amazon RDS Multi-AZ** existe justamente para reduzir esse risco.

A ideia é simples:

> **Primary em uma AZ + Standby em outra AZ + replicação síncrona + failover automático.**

E aqui está a primeira regra que você precisa guardar:

**Multi-AZ é principalmente sobre Alta Disponibilidade (HA), não sobre aumentar performance de leitura.**

Se o problema é excesso de consultas de leitura, pense em **Read Replicas**.

---

## 1. O Cenário: Por que e quando ativar?

Você usa Multi-AZ quando a aplicação precisa continuar disponível mesmo diante de uma falha na infraestrutura de uma AZ.

### O que o Multi-AZ resolve?

- **Falha de hardware:** se a instância Primary apresentar um problema grave, existe uma Standby pronta para assumir.
- **Falha de uma AZ:** a Standby fica em outra Zona de Disponibilidade.
- **Alta disponibilidade:** o RDS pode realizar o failover automaticamente.
- **Redução de downtime:** a aplicação não precisa ser configurada novamente para apontar para outro banco.

### O que o Multi-AZ NÃO resolve?

**Performance de leitura.**

Imagine este cenário:

> Seu e-commerce está recebendo milhares de consultas por segundo e os relatórios estão deixando o banco lento.

Criar uma Standby Multi-AZ não vai distribuir essas consultas.

A Standby tradicional do Multi-AZ fica aguardando um eventual failover.

Para distribuir consultas de leitura, a solução adequada é utilizar **Read Replicas**.

> **Macete de prova:**  
> **Multi-AZ = disponibilidade.**  
> **Read Replica = leitura.**

---

## 2. Passo a Passo no Console AWS

Para criar um banco resiliente, a lógica no console segue este fluxo.

### Passo 1: Escolha do Motor (Engine)

No console do RDS, ao selecionar **Create database**, você escolhe o mecanismo do banco, como:

- MySQL;
- PostgreSQL;
- MariaDB;
- Oracle;
- Microsoft SQL Server.

O suporte e as opções exatas de Multi-AZ variam de acordo com o engine e o tipo de deployment escolhido.

Para a CLF-C02, porém, o mais importante é entender o conceito:

**RDS Multi-AZ = banco relacional gerenciado com uma instância Standby em outra AZ.**

---

### Passo 2: Configuração de Disponibilidade

A configuração fica na seção relacionada a **Availability & Durability**.

Você deve escolher uma opção de deployment **Multi-AZ**, como a criação de uma instância Standby em outra AZ.

Para isso, o **DB Subnet Group** precisa disponibilizar subnets em múltiplas Availability Zones dentro da mesma região.

Pense assim:

~~~mermaid
flowchart LR

    subgraph REGION["☁️ AWS Region"]
        
        subgraph AZA["Availability Zone A"]
            PRIMARY["🗄️ RDS<br/>Primary"]
        end

        subgraph AZB["Availability Zone B"]
            STANDBY["🗄️ RDS<br/>Standby"]
        end

        PRIMARY <-->|"Replicação síncrona"| STANDBY

    end

    classDef primary fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef standby fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;

    class PRIMARY primary;
    class STANDBY standby;
~~~

---

## 3. O que acontece nos bastidores?

Depois da criação, o RDS mantém:

1. Uma instância **Primary**, que atende as operações normais da aplicação.
2. Uma instância **Standby**, localizada em outra AZ.
3. **Replicação síncrona** entre Primary e Standby.

A Standby não é uma réplica de leitura.

Ela está ali principalmente para assumir o papel da Primary caso seja necessário realizar um failover.

### O fluxo normal

~~~mermaid
flowchart LR

    APP["🖥️ Aplicação"]
        --> ENDPOINT["🔗 RDS Endpoint"]
        --> PRIMARY["🗄️ RDS Primary"]

    PRIMARY -->|"Replicação síncrona"| STANDBY["🗄️ RDS Standby<br/>Outra AZ"]

    classDef app fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef endpoint fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef primary fill:#F3E5F5,stroke:#8E24AA,stroke-width:2px;
    classDef standby fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;

    class APP app;
    class ENDPOINT endpoint;
    class PRIMARY primary;
    class STANDBY standby;
~~~

A aplicação lê e grava na **Primary**.

A Standby recebe os dados por meio da replicação síncrona e permanece pronta para assumir caso ocorra uma falha.

---

## 4. O Failover Automático

Agora vem a parte que mais interessa para a prova.

Imagine que a Primary fique indisponível.

O RDS detecta a falha e pode realizar um **automatic failover** para a Standby.

O fluxo fica assim:

### Antes da falha

~~~mermaid
flowchart LR

    APP["🖥️ Aplicação"]
        --> ENDPOINT["🔗 RDS Endpoint"]
        --> PRIMARY["🗄️ Primary<br/>AZ-A"]

    PRIMARY -->|"Replicação síncrona"| STANDBY["🗄️ Standby<br/>AZ-B"]

    classDef app fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef endpoint fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef primary fill:#F3E5F5,stroke:#8E24AA,stroke-width:2px;
    classDef standby fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;

    class APP app;
    class ENDPOINT endpoint;
    class PRIMARY primary;
    class STANDBY standby;
~~~             AZ-B

### Depois do failover

~~~mermaid
flowchart LR

    APP["🖥️ Aplicação"]
        --> ENDPOINT["🔗 RDS Endpoint"]
        --> STANDBY["🗄️ Standby<br/>AZ-B"]

    STANDBY -->|"Após failover"| ACTIVE["🟢 Nova Primary"]

    classDef app fill:#E3F2FD,stroke:#1565C0,stroke-width:2px;
    classDef endpoint fill:#FFF8E1,stroke:#F9A825,stroke-width:2px;
    classDef standby fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px;
    classDef active fill:#E0F2F1,stroke:#00796B,stroke-width:2px;

    class APP app;
    class ENDPOINT endpoint;
    class STANDBY standby;
    class ACTIVE active;
~~~

A grande sacada é que a aplicação continua usando o **mesmo endpoint lógico do RDS**.

O RDS atualiza o DNS associado ao endpoint para direcionar as conexões para a instância que assumiu o papel de Primary.

Você **não precisa alterar a URL do banco no código da aplicação**.

Durante o processo, as conexões existentes podem ser interrompidas e a aplicação precisa reconectar. O tempo de recuperação depende do cenário e do engine, portanto não trate um número exato de segundos como regra universal.

> **Pegadinha:** não pense "o endpoint mudou".  
> O endpoint continua sendo o ponto de acesso da aplicação; o RDS altera para onde ele resolve durante o failover.

---

## 5. A Batalha Final: Multi-AZ vs. Read Replicas

Não confunda os dois.

É exatamente aqui que a banca pode montar uma questão aparentemente simples e colocar dois serviços que parecem resolver o mesmo problema.

| Característica | Multi-AZ Deployment | Read Replicas |
| :--- | :--- | :--- |
| **Objetivo principal** | Alta disponibilidade / failover | Escalabilidade de leitura |
| **Replicação** | **Síncrona** | **Assíncrona** |
| **Standby atende leituras?** | **Não**, no deployment tradicional | **Sim** |
| **Failover automático** | **Sim** | Não como mecanismo padrão da réplica |
| **Pode receber tráfego da aplicação?** | Primary atende o tráfego normal | Réplicas podem atender leituras |
| **Cross-Region** | O Multi-AZ tradicional ocorre dentro da mesma região | Read Replicas podem ser criadas em outra região |
| **Uso típico** | Sobreviver a falhas | Distribuir consultas de leitura |
| **Consistência** | Replicação síncrona entre Primary e Standby | Pode existir atraso de replicação |
| **Promoção** | Standby assume automaticamente em um failover | Réplica pode ser promovida manualmente |

### Grave esta diferença

**Multi-AZ:**

> "Minha aplicação precisa continuar disponível se o banco principal falhar."

**Read Replica:**

> "Minha aplicação está fazendo leitura demais e preciso distribuir essas consultas."

Essa distinção resolve uma quantidade absurda de questões.

---

## 6. E o Backup?

Existe outra vantagem importante no deployment Multi-AZ.

Para deployments Multi-AZ de instância, o RDS pode realizar o backup automatizado a partir da **Standby**, quando disponível, reduzindo o impacto de I/O na Primary.

Isso não significa que Multi-AZ substitui uma estratégia de backup.

São problemas diferentes:

- **Multi-AZ:** disponibilidade diante de falhas.
- **Backup:** recuperação de dados.
- **Read Replica:** escalabilidade de leitura.

E tem mais uma diferença importante:

> **Multi-AZ não é uma estratégia completa de Disaster Recovery.**

Ele protege principalmente contra falhas dentro de uma região, como a indisponibilidade de uma AZ.

Se o requisito for recuperação após um desastre regional, você precisa pensar em estratégias adicionais, como backups, réplicas cross-Region ou outras arquiteturas de DR.

---

## 🎯 Gatilho de Exame

Fique esperto com estes termos em inglês.

Se aparecerem no enunciado, pense imediatamente no conceito correspondente:

### **RDS Multi-AZ deployment**

→ **Alta disponibilidade**

Procure por cenários envolvendo falha de infraestrutura, disponibilidade e failover automático.

### **Automatic failover**

→ **Standby assume o papel da Primary**

A troca acontece sem você precisar promover manualmente a Standby.

### **Synchronous replication**

→ **Primary + Standby**

Os dados são replicados de forma síncrona entre as instâncias do deployment Multi-AZ.

### **Read replicas**

→ **Escalabilidade de leitura**

Se o problema é uma aplicação fazendo muitas consultas de leitura, pense em Read Replicas.

### **Cross-Region read replica**

→ **Leitura + possibilidade de estratégia entre regiões**

Read Replicas podem ser utilizadas em outra região, dependendo do engine e da configuração.

### **No impact on Primary during backup**

→ **Backup automatizado usando a Standby, quando aplicável**

Em deployments Multi-AZ de instância, isso pode reduzir o impacto de I/O na Primary.

> **Atenção:** não transforme isso em uma regra para todos os tipos de RDS. O comportamento depende do tipo de deployment e do engine.

---

## 🧠 Mapa Mental de 30 Segundos

Se a questão falar em...

| Enunciado | Pense em... |
| :--- | :--- |
| **Alta disponibilidade** | Multi-AZ |
| **Failover automático** | Multi-AZ |
| **Falha de uma AZ** | Multi-AZ |
| **Standby em outra AZ** | Multi-AZ |
| **Replicação síncrona** | Multi-AZ |
| **Escalar leituras** | Read Replica |
| **Muitas consultas SELECT** | Read Replica |
| **Replicação assíncrona** | Read Replica |
| **Réplica em outra região** | Read Replica |
| **Recuperação de dados** | Backup / Snapshot |
| **Disaster Recovery regional** | Estratégia de DR adicional |

---

## 🚨 Sinal de Alerta

A **Standby do Multi-AZ tradicional NÃO deve ser usada para leitura**.

Se a questão disser:

> "A empresa precisa aumentar a capacidade de leitura do banco."

Não escolha Multi-AZ.

Pense em:

**Read Replica.**

Se disser:

> "A empresa precisa garantir que o banco continue disponível caso a AZ principal falhe."

Agora sim:

**RDS Multi-AZ.**

E se disser:

> "A empresa precisa recuperar dados após exclusão acidental."

Também não é simplesmente Multi-AZ.

Pense em:

**Backup / Snapshot / estratégia de recuperação.**

### A regra que salva questão

> **Multi-AZ = "se meu banco morrer, outro assume."**
>
> **Read Replica = "meu banco está recebendo leitura demais."**
>
> **Backup = "preciso recuperar meus dados."**

Dica: se você lembrar dessas três frases na hora da prova, já elimina uma boa parte das pegadinhas de RDS.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 5: Mnemônicos e Regras de Ouro - Bancos de Dados e Analytics](09-mnemonicos-bancos-de-dados.md)
* [➡️ Módulo 5: Micro-Simulado - Bancos de Dados e Analytics](11-micro-simulado-bancos-de-dados.md)

---
---