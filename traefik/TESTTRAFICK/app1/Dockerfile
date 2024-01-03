FROM nginx:alpine

COPY nginx.conf nginx.conf
COPY ./conf.d/* /etc/nginx/conf.d/
COPY ./html/* /var/www/html/

# Crée le groupe www avec l'ID 1000
# Crée l'utilisateur www avec l'ID 1000, ajouté au groupe www,
# et le répertoire de travail est /var/www/html
RUN addgroup -g 1000 www \
    && adduser -D -u 1000 -G www -h /var/www/html www \
    && chown -R www:www /var/www/html

# Donne des droits d'écriture au groupe www sur le répertoire html
RUN chmod -R g+w /var/www/html

# # L'utilisateur www a les droits nécessaires pour exécuter nginx
# USER www

ENTRYPOINT ["nginx", "-g", "daemon off;"]
