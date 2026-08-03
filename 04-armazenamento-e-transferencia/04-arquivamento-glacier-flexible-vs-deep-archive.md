# Arquivamento: Glacier Flexible Retrieval vs. Deep Archive

Nem todo arquivo precisa ficar disponível em segundos. Pense em backups antigos, documentos fiscais, registros de auditoria ou arquivos que a empresa é obrigada a guardar por anos. Eles quase nunca são acessados, então faz sentido armazená-los na camada mais barata possível.

É exatamente para esse cenário que existem o **S3 Glacier Flexible Retrieval** e o **S3 Glacier Deep Archive**.

---

## 1. O Propósito do Arquivamento de Longo Prazo

O objetivo dessas classes é simples: **reduzir drasticamente o custo de armazenamento** para dados que ficaram "frios".

Na prática, elas são usadas para:

- **Backups históricos:** cópias antigas que dificilmente precisarão ser restauradas.
- **Compliance:** documentos exigidos por normas ou legislações, mesmo que ninguém os consulte por anos.
- **Logs e auditorias:** registros mantidos apenas para eventuais investigações futuras.
- **Arquivos históricos:** dados importantes que precisam ser preservados, mas não utilizados diariamente.

A lógica é simples:

- quanto menos frequência de acesso;
- quanto maior o tempo que você pode esperar pela recuperação;

➡️ menor será o custo de armazenamento.

> **Pegadinha de prova:** Glacier não serve para economizar em arquivos que você acessa toda semana. Ele existe para dados realmente "frios".

---

## 2. Amazon S3 Glacier Flexible Retrieval

Antigamente conhecido apenas como **Amazon Glacier**, essa é a classe indicada para arquivos que ficam meses sem acesso, mas que eventualmente precisam ser recuperados.

Imagine:

- um backup mensal de um banco de dados;
- registros de auditoria do semestre passado;
- documentos antigos que podem ser solicitados durante uma fiscalização.

Você raramente acessa esses arquivos, mas quando precisar deles, aceita esperar alguns minutos ou horas.

### Opções de Recuperação

Você escolhe quanto quer pagar pela velocidade de recuperação:

| Opção | Tempo de recuperação | Quando usar |
| :--- | :--- | :--- |
| **Expedited** | 1 a 5 minutos | Situações urgentes, como auditorias inesperadas. |
| **Standard** | 3 a 5 horas | Opção equilibrada entre custo e tempo. |
| **Bulk** | 5 a 12 horas | Recuperações em massa, com menor custo. |

### Retenção mínima

Os objetos devem permanecer armazenados por **90 dias**.

Se forem removidos antes desse período, a AWS cobra uma **taxa de exclusão antecipada (Early Deletion Fee)**.

---

## 3. Amazon S3 Glacier Deep Archive

Se o Flexible Retrieval é um congelador, o **Deep Archive** é praticamente um cofre lacrado.

Ele oferece **o menor custo de armazenamento da AWS**, mas cobra esse preço exigindo muita paciência na recuperação.

É indicado para dados que provavelmente nunca serão acessados, mas que precisam ser preservados.

Alguns exemplos:

- documentos fiscais guardados por obrigação legal;
- prontuários e registros corporativos;
- backups anuais;
- arquivos históricos mantidos por 7, 10 ou mais anos.

### Opções de Recuperação

Aqui não existe recuperação rápida.

| Opção | Tempo de recuperação |
| :--- | :--- |
| **Standard** | Cerca de 12 horas |
| **Bulk** | Até 48 horas |

Se precisar do arquivo imediatamente, você escolheu a classe errada.

### Retenção mínima

Os objetos devem permanecer armazenados por pelo menos **180 dias**.

Assim como no Flexible Retrieval, remover antes desse prazo gera cobrança de exclusão antecipada.

> **Esse é um dos cenários favoritos da CLF-C02:** se o enunciado disser que o tempo de recuperação **não é importante** e o objetivo é **minimizar custos**, normalmente o gabarito será **Glacier Deep Archive**.

---

## 4. Retenção e Penalidades por Exclusão Antecipada

Uma dúvida comum é:

"Se o armazenamento é tão barato, por que existe tempo mínimo?"

Porque a AWS calcula esses preços considerando que os dados ficarão armazenados por bastante tempo.

Por isso existem períodos mínimos de retenção:

- **Glacier Flexible Retrieval:** 90 dias.
- **Glacier Deep Archive:** 180 dias.

Se um arquivo for apagado antes desse prazo, a AWS cobra o valor correspondente ao período restante.

### Exemplo

Imagine que você envie um backup para o **Deep Archive** hoje.

Depois de apenas **30 dias**, decide apagá-lo.

Mesmo sem o arquivo existir mais, a AWS cobrará como se ele tivesse permanecido pelos **180 dias mínimos**.

Por isso, essas classes fazem sentido apenas para dados realmente destinados ao arquivamento de longo prazo.

---

## 5. Matriz de Decisão Rápida

| Requisito | Glacier Flexible Retrieval | Glacier Deep Archive |
| :--- | :--- | :--- |
| **Custo de armazenamento** | Muito baixo | **O menor da AWS** |
| **Recuperação em minutos** | Sim (Expedited) | Não |
| **Tempo típico de recuperação** | Minutos ou horas | 12 a 48 horas |
| **Retenção mínima** | 90 dias | 180 dias |
| **Ideal para** | Backups raramente acessados | Arquivamento legal e histórico de longo prazo |

---

## 🎯 Gatilho de Exame

Se aparecerem estes termos, pense imediatamente em Glacier:

- **S3 Glacier Flexible Retrieval:** arquivamento com possibilidade de recuperar dados em minutos ou horas.
- **S3 Glacier Deep Archive:** armazenamento de menor custo para dados acessados muito raramente.
- **Long-term data archiving:** arquivamento de longo prazo.
- **Compliance retention:** retenção de dados por exigências legais ou regulatórias.
- **Retrieval time:** tempo necessário para recuperar um objeto arquivado.
- **Early deletion fee:** cobrança por excluir objetos antes do período mínimo de retenção.

> **Sinal de Alerta:** Não confunda o **Glacier Deep Archive** com o **Glacier Instant Retrieval**. Se o enunciado disser que os dados são raramente acessados, **mas precisam estar disponíveis imediatamente (milissegundos)**, a resposta é **Glacier Instant Retrieval**. Se puder esperar horas para economizar o máximo possível, escolha **Glacier Deep Archive**.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 4: Amazon EFS - Arquivos Compartilhados e a Magia do NFS](03-efs-sistema-arquivos-compartilhado-nfs.md)
* [➡️ Módulo 4: Família AWS Snow - Migração Física e Offline](05-migracao-fisica-familia-snow-offline.md)

---
---