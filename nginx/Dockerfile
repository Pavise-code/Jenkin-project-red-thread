FROM nginx:latest

# On définit le dossier de travail
WORKDIR /var/www/html

# On copie la configuration
COPY nginx.conf /etc/nginx/conf.d/default.conf

# TRÈS IMPORTANT : On copie aussi les fichiers du site (dont le style.css)
# pour que Nginx puisse les servir au navigateur
COPY ../app /var/www/html