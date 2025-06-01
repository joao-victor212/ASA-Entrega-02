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
├── service.bat
└── service.sh
```

---

##    Passo a passo

### 🐳 Subir Todos os Containers com um Único Comando

#### 1️⃣ Parar e remover containers existentes

```bash
docker stop web bind9 adminer 2>/dev/null
docker rm web bind9 adminer 2>/dev/null
```

#### 2️⃣ Criar rede Docker (se não existir)
```bash
docker network create asa_rede 2>/dev/null || true
```

#### 3️⃣ Construir e subir containers
```bash
cd DNS && docker build -t meu_bind9 . && docker run -d --name bind9 --network asa_rede -p 53:53/udp meu_bind9 && cd ..
cd WEB && docker build -t meu_web . && docker run -d --name web --network asa_rede -p 8080:80 meu_web && cd ..
docker run -d --name adminer --network asa_rede -p 8081:8080 adminer:latest
```

#### 4️⃣ Verificar status
```bash
echo ""
echo "✅ CONTAINERS INICIADOS COM SUCESSO!"
echo "===================================="
echo "WEB:      http://localhost:8080"
echo "Adminer:  http://localhost:8081"
echo "           (Servidor: db, Usuário: admin, Senha: senha)"
echo ""
docker ps --format "table {{.Names}}\t{{.Status}}\t{{.Ports}}"
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

### 🖧 1. **Servidor DNS (Bind9)**
- Configurado com zona primária `asa.br`
- Permite a resolução dos domínios locais (ex: `web1.asa.br`, `web2.asa.br`)

### 🌐 2. **Proxy Reverso HTTP + HTTPS (NGINX)**
- Redireciona requisições para os servidores `web1` e `web2`
- Configurado com **certificados SSL autoassinados**
- Acessível via HTTPS em `https://localhost`

### 🖥️ 3. **Servidores Web**
- `WEB1`: Página personalizada em `index.html`
- `WEB2`: Página diferenciada com identificação própria

---

## 🏗️ Componentes da Solução

-Docker Engine
-Docker Compose
-Bind9 (DNS)
-NGINX (Proxy Reverso)
-SSL/TLS (certificados autoassinados)
-Redes Docker personalizadas
-HTML estático

---

## ▶️ Execução do Projeto

### Pré-requisitos

- Docker instalado → [Instalar Docker](https://docs.docker.com/get-docker/)
- Docker Compose instalado → [Instalar Docker Compose](https://docs.docker.com/compose/install/)

### Como rodar

```bash
git clone https://github.com/joao-victor212/ASA-Entrega-02.git
cd ASA-Entrega-02
docker compose up --build

---

## 🗣️ Apresentação

A apresentação aborda:
- Conceitos teóricos do Docker
- Explicação do cenário proposto
- Demonstração prática com containers em execução
- Vídeo explicativo da atividade

📎 Arquivos disponíveis em `docs/`

---

## 👥 Equipe

- José Eduardo Bezerra de Medeiros - [@eduardobezerraz](https://github.com/eduardobezerraz)
- João Marcos Medeiros Costa - [@joaommcjm](https://github.com/joaommcjm)
- João Victor do Nascimento Mendonça - [@joao-victor212](https://github.com/joao-victor212)

---
