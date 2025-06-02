# 🚢 ASA - Entrega 02: Infraestrutura com Docker, DNS e HTTP com SSL

Este repositório contém a entrega da Atividade 02 da disciplina de **Administração de Serviços em Ambientes Computacionais (ASA)**.  
O principal objetivo é **consolidar os conceitos de Docker**, com a **implementação de serviços reais** como DNS, proxy reverso HTTP com SSL e múltiplos servidores web usando containers Docker.

🔗 [Dicas e informações da atividade original](https://github.com/salesfilho/learning-asa/blob/4-Docker%2BDNS%2BHTTP/README.md)

---

## 🧠 Objetivos

- Aplicar os conhecimentos básicos de Docker e Docker Compose
- Implementar uma infraestrutura com múltiplos containers
- Configurar servidor DNS com zona primária
- Configurar proxy reverso com SSL (HTTPS)
- Gerenciar múltiplos serviços web em containers
- Trabalhar de forma colaborativa em equipe utilizando Git e GitHub

---

## 📁 Estrutura do Projeto


```
ASA-Entrega-02/
├── DNS/
│   ├── Dockerfile
│   ├── db.asa.br
│   └── named.conf.local
├── WEB1/
│   ├── Dockerfile
│   └── index.html
├── WEB2/
│   ├── Dockerfile
│   └── index.html
├── PROXY/
│   ├── 404.html
│   └── index.html
│   ├── Dockerfile
│   └── default.conf
├── README.md
├── docker-compose.yml

```
---

## 🔧 Tecnologias Utilizadas

- Docker
- Docker Compose
- Ubuntu/Debian (base dos containers)
- Servidores HTTP/DNS (Apache/Nginx e Bind)
- Git + GitHub

---

## 🏗️ Componentes da Solução

### 🖧 1. Servidor DNS (Bind9)
- Configurado com uma **zona primária** `asa.br`
- Responsável pela **resolução de nomes locais**, como:
  - `web1.asa.br`
  - `web2.asa.br`

### 🌐 2. Proxy Reverso HTTP + HTTPS (NGINX)
- Implementado com **NGINX**
- Redireciona requisições para os servidores web conforme o domínio requisitado
- Protegido com **certificados SSL autoassinados**

### 🖥️ 3. Servidores Web (WEB1 e WEB2)
- **WEB1:** Página HTML personalizada identificando o serviço
- **WEB2:** Página HTML diferente da WEB1 para fácil distinção

---

### ⚙️ Tecnologias e Conceitos Envolvidos

- **Docker Engine:** Motor principal de containers
- **Docker Compose:** Orquestração de múltiplos containers
- **Bind9:** Servidor DNS com zona configurável
- **NGINX:** Proxy reverso com suporte a SSL
- **SSL/TLS:** Certificados autoassinados para comunicação segura
- **Redes Docker personalizadas:** Permite comunicação entre containers isoladamente
- **HTML Estático:** Conteúdo servido pelas aplicações web

---

## ▶️ Execução do Projeto

### Pré-requisitos

- Docker instalado → [Instalar Docker](https://docs.docker.com/get-docker/)
- Docker Compose instalado → [Instalar Docker Compose](https://docs.docker.com/compose/install/)

### ▶️ Como rodar

#### 🔧⚠️ Configuração do arquivo hosts para teste local
Para que os nomes de domínio funcionem corretamente no seu PC local, você DEVE editar o arquivo hosts com permissão de administrador:
- WINDOWS: 
  Abra o terminal como adiministrador e execute o seguinte comando:
```bash
notepad C:\Windows\System32\drivers\etc\hosts
```
- Linux/macOS:
  sudo nano /etc/hosts

  - Adicone as seguintes linhas ao arquivo e salve.
  ```bash
  127.0.0.1    asa.br
  127.0.0.1    web1.asa.br
  127.0.0.1    web2.asa.br
  ```

```bash
git clone https://github.com/joao-victor212/ASA-Entrega-02.git
cd ASA-Entrega-02
docker compose up --build
```

---

## 👥 Equipe

- José Eduardo Bezerra de Medeiros - [@eduardobezerraz](https://github.com/eduardobezerraz)
- João Marcos Medeiros Costa - [@joaommcjm](https://github.com/joaommcjm)
- João Victor do Nascimento Mendonça - [@joao-victor212](https://github.com/joao-victor212)

---
