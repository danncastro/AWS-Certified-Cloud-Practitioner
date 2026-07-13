# 🧪 Lab: Explorando a Infraestrutura Global da AWS

Mano, papo reto, a nuvem não é uma "caixa mágica" perdida na internet.

Ela é composta por:

- data centers;
- servidores;
- fibras ópticas;
- equipamentos de rede;
- infraestrutura física distribuída pelo mundo.

Neste laboratório você vai visualizar como a AWS organiza toda essa estrutura e entender, na prática, por que **Regiões**, **Availability Zones** e **Latência** são conceitos tão importantes.

---

## 🎯 1. Objetivo do Lab
O foco aqui é prático e visual. Você vai:
*   Identificar os códigos oficiais das **Regions** (ex: `us-east-1`, `sa-east-1`).
*   Entender a anatomia das **Availability Zones (AZs)**.
*   Sentir o impacto real da **Latency** (latência) na escolha de uma região.

---

## 2. Passo a Passo Guiado

### Parte 1: Visualização Interativa (Sem Conta AWS)
Se você ainda não tem uma conta, relaxa. A AWS mantém um site interativo animal para isso:
1.  Acesse o [AWS Global Infrastructure Features](https://infrastructure.aws/).
2.  Navegue pelo mapa mundi. Observe os pontos azuis (**Regions**) e como elas estão espalhadas. Cada Região é um conjunto independente de infraestrutura.
3.  Passe o mouse sobre a Região de São Paulo. Veja que o código é `sa-east-1` e que ela possui, atualmente, 3 **Availability Zones**. Isso significa que existem 3 data centers independentes trabalhando em conjunto.

Exemplo:

| Região | Código |
|---------|--------|
| São Paulo | `sa-east-1` |
| N. Virginia | `us-east-1` |
| Ohio | `us-east-2` |
| Tóquio | `ap-northeast-1` |

---

### Parte 2: Explorando via Console (*Se tiver conta*)
1.  Faça login no **AWS Management Console**.
2.  Olhe para o canto superior direito, ao lado do seu nome de usuário. Ali está o **Region Selector**.
3.  Clique e alterne entre "N. Virginia" (`us-east-1`) e "São Paulo" (`sa-east-1`). Perceba que a lista de recursos (como instâncias EC2) muda completamente; Isso acontece porque os serviços são **Regionais**. as regiões são **geograficamente isoladas**. Uma instância EC2 criada em São Paulo não aparece automaticamente na Virgínia.
4.  Vá até o painel do serviço **VPC** e clique em **Subnets**. Observe que cada Subnet está obrigatoriamente vinculada a uma AZ específica (ex: `sa-east-1a`). Cada subnet existe em apenas uma AZ.

---

## 3. O Mistério da AZ Randomization

Aqui está uma malandragem técnica que cai em prova: os IDs das AZs.
Você pode ver nomes como `us-east-1a` ou `us-east-1b`. Mas se liga: o que é a zona "A" na minha conta pode ser a zona "C" na sua conta. Na verdade, elas podem representar exatamente o mesmo data center físico.

**Por que a AWS faz isso?**
Para evitar que todo mundo suba recursos na zona "A" por ser a primeira da lista e sobrecarregue um único data center físico. Para identificar o data center físico real, usamos o **Availability Zone ID** (ex: `use1-az1`), esse identificador é único e representa o data center físico real.

Ao contrário dos nomes (`us-east-1a`, `us-east-1b`...), o **AZ ID** é consistente entre diferentes contas.

---

## 4. Desafio Prático: Teste de Latência

Agora vamos medir o tempo de resposta entre sua localização e diferentes Regiões AWS.

A latência é o tempo que o dado leva para ir e voltar. Vamos provar por que a proximidade importa:
1.  Acesse o site [cloudping.info](https://www.cloudping.info/).
2.  Clique em **HTTP Ping**.
3.  Compare os resultados:
    *   Qual a latência para a região mais próxima de você?
    *   Qual a latência para a Virgínia (`us-east-1`)?
    *   Qual a latência para Tóquio (`ap-northeast-1`)?

Exemplo:

| Região | Código | Latência |
|---------|--------|----------|
| São Paulo | `sa-east-1` | Menor latência (para usuários no Brasil) |
| N. Virginia | `us-east-1` | Latência intermediária |
| Tóquio | `ap-northeast-1` | Latência muito maior |

Os valores variam conforme sua localização.

**Conclusão do Dev:** Se o seu cliente está no Brasil, hospedar em Tóquio vai deixar o app "lagado". A proximidade geográfica reduz a latência e melhora a experiência do usuário.

---

### Imagine dois cenários.

#### Cenário A

| Usuário:| Servidor:| Resultado:|
|-|-|-|
| 📍 São Paulo | 📍 São Paulo | baixa latência; |
||| resposta rápida. |

---

#### Cenário B

| Usuário: | Servidor: | Resultado: |
|-|-|-|
| 📍 São Paulo | 📍 Tóquio | maior tempo de resposta; |
||| mais atrasos na comunicação; |
||| pior experiência para o usuário. |

---

#### Conclusão

Quanto mais próxima estiver a infraestrutura do usuário final...

Menor será a latência.

Por isso a escolha da Região é uma decisão importante de arquitetura.

---

## 🎯 Gatilho de Exame

Mapeie esses termos práticos para as questões teóricas:

*   **Region code:** O identificador curto (ex: `us-east-1`). Essencial para scripts de automação.
*   **Availability Zone ID:** O código que identifica o data center físico real, ignorando a randomização de nomes.
*   **Latency check:** Processo de validar a velocidade de resposta; critério principal para escolher onde colocar o workload.
*   **Switching regions:** Ação de mudar o contexto geográfico no console. Lembre-se: serviços são regionais por padrão (exceto IAM, Route 53 e CloudFront).
*   **Isolated geographic area:** Definição de Região que a AWS sempre usa para testar se você sabe que uma não afeta a outra.

---

## 🚨 Pegadinhas de Prova

### Recursos Regionais

A maioria dos serviços da AWS é regional.

Exemplos:

- Amazon EC2;
- Amazon RDS;
- Amazon VPC;
- Amazon EKS.

Se você trocar de Região no Console, esses recursos deixam de aparecer.

---

### Serviços Globais

Alguns serviços não dependem da Região.

Exemplos:

- IAM;
- Amazon Route 53;
- Amazon CloudFront.

Esses serviços continuam acessíveis independentemente da Região selecionada.

---

### Amazon S3

O Console do Amazon S3 é global. Porém...

Cada Bucket pertence a uma Região específica.

Se um Bucket foi criado em:

```
sa-east-1
```

Ele continuará armazenando seus dados nessa Região, mesmo que você esteja navegando pelo Console em outra Região.

---

## ✅ Checklist do Laboratório

Ao concluir este laboratório, confirme se você conseguiu:

- [ ] Identificar os códigos das principais AWS Regions.
- [ ] Navegar entre diferentes Regiões no Console AWS.
- [ ] Entender a função das Availability Zones.
- [ ] Compreender a diferença entre AZ Name e AZ ID.
- [ ] Medir a latência entre diferentes Regiões utilizando o CloudPing.
- [ ] Entender por que a proximidade geográfica melhora a experiência do usuário.
- [ ] Diferenciar serviços regionais de serviços globais.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Mnemônicos e Revisão: Fundamentos e Infraestrutura Global](08-mnemonicos-fundamentos.md)
* [➡️ Micro-Simulado: Fundamentos e Infraestrutura Global](10-micro-simulado-fundamentos.md)

---
---