FROM nginx

# Atualiza o apt e instala o ping
RUN apt-get update && apt-get install -y iputils-ping

# Copia o index.html para o diretório padrão do Nginx
COPY index.html /usr/share/nginx/html/index.html
