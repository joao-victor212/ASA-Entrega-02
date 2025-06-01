<<<<<<< HEAD
FROM nginx:alpine

# Copia a configuração padrão para o NGINX
COPY default.conf /etc/nginx/conf.d/default.conf

# Copia a página inicial do proxy
COPY index.html /usr/share/nginx/html/index.html

# Copia a página de erro 404
COPY 404.html /usr/share/nginx/html/404.html
=======
FROM nginx:latest

# Copia a configuracao do servidor
COPY default.conf /etc/nginx/conf.d

# Copia a pagina personalizada para a imagem do servidor
COPY index.html /usr/share/nginx/html
>>>>>>> ad2137e25df056a62956438c28bc352340aba558
