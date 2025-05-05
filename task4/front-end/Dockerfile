# Utilisation de l'image Nginx la plus récente comme base
FROM nginx:latest

# Copie des fichiers du frontend dans le repertoire
COPY ./softy-pinko-front-end /var/www/html/softy-pinko-front-end

# Copie du fichier de configuration Nginx
COPY ./softy-pinko-front-end.conf /etc/nginx/conf.d/default.conf

# Exposition du port 9000
EXPOSE 9000
