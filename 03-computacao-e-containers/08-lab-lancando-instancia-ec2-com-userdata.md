# Lab: Lançando uma Instância EC2 com User Data

Subir uma instância clicando em botão é ótimo para aprender, mas no dia a dia o objetivo é automatizar tudo. Com **User Data**, a instância já nasce configurada, instalando pacotes e executando tarefas automaticamente no **primeiro boot**.

Neste lab, vamos criar uma instância EC2 que já inicia com o **Apache** instalado e pronto para servir uma página web.

---

## 1. Objetivos do Lab

Ao final deste laboratório você será capaz de:

- Criar uma instância usando o **EC2 Launch Wizard**.
- Configurar um **Security Group** para acesso HTTP.
- Automatizar a instalação do Apache usando **User Data**.
- Validar o acesso ao servidor via navegador.

---

## 2. Passo a Passo

### Passo 1 — Criando a Instância

1. Acesse **EC2** → **Launch instance**.
2. Defina um nome, por exemplo: `meu-servidor-web`.
3. Escolha a AMI **Amazon Linux 2023** (*Free Tier Eligible*).
4. Selecione uma instância **t2.micro** ou **t3.micro**.

### Passo 2 — Key Pair

- Utilize uma chave existente ou crie uma nova.
- Faça o download do arquivo `.pem`.

> **Dica:** Neste laboratório o acesso SSH não será necessário, pois toda a configuração será feita pelo User Data.

### Passo 3 — Security Group

Em **Network settings**:

- Mantenha a porta **22 (SSH)** liberada para seu IP.
- Adicione uma regra:

| Tipo | Porta | Origem |
|------|------:|--------|
| HTTP | 80 | Anywhere (0.0.0.0/0) |

---

### Passo 4 — Configurando o User Data

Em **Advanced details**, cole o script abaixo no campo **User Data**.

```bash
#!/bin/bash

yum update -y
yum install -y httpd

systemctl start httpd
systemctl enable httpd

echo "<h1>Papo Reto AWS: Servidor rodando na instancia $(hostname -f)</h1>" > /var/www/html/index.html
```

---

## 3. O que esse Script Faz?

| Comando | Função |
|---------|--------|
| `yum update -y` | Atualiza os pacotes do sistema. |
| `yum install -y httpd` | Instala o Apache. |
| `systemctl start httpd` | Inicia o serviço. |
| `systemctl enable httpd` | Inicializa o Apache automaticamente nos próximos boots. |
| `echo ... > index.html` | Cria a página inicial do servidor. |

---

## 4. Validando o Lab

1. Clique em **Launch instance**.
2. Aguarde o estado **Running**.
3. Copie o **Public IPv4 Address**.
4. Abra o navegador acessando:

```
http://IP_DA_INSTANCIA
```

Se tudo estiver correto, será exibida a página criada pelo script do User Data.

```mermaid
graph LR
    A[Launch Instance] --> B[User Data]
    B --> C[Instala Apache]
    C --> D[Inicia Serviço]
    D --> E[Cria index.html]
    E --> F[Servidor Web Disponível]
```

---

## 🎯 Gatilho de Exame

Se aparecerem estes termos, faça a associação imediatamente:

- **EC2 Launch Wizard** → Assistente de criação da instância.
- **User Data** → Script executado automaticamente no primeiro boot.
- **Bootstrapping** → Configuração inicial automática da instância.
- **Apache (`httpd`)** → Servidor web utilizado em laboratórios.
- **Security Group (HTTP 80)** → Permite acesso à aplicação via navegador.

> **Sinal de Alerta:** O **User Data** normalmente executa apenas no **primeiro boot** da instância. Reiniciar a máquina (**Reboot**) não executa o script novamente.

---

### 🧭 Navegação de Conteúdos
* [🏠 Menu Principal](../README.md)
* [⬅️ Módulo 3: Mnemônicos e Atalhos - O Guia de Sobrevivência em Computação](07-mnemonicos-computacao.md)
* [➡️ Módulo 3: Micro-Simulado - Computação e Containers](09-micro-simulado-computacao.md)

---
---