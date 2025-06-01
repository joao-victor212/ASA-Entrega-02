FROM nginx:alpine

# Copia a configuração padrão para o NGINX
COPY default.conf /etc/nginx/conf.d/default.conf

# Copia a página inicial do proxy
COPY index.html /usr/share/nginx/html/index.html

# Copia a página de erro 404
COPY 404.html /usr/share/nginx/html/404.html
