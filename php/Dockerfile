FROM php:8.1-fpm

# Installation des extensions
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli

# 1. On définit le dossier de travail
WORKDIR /var/www/html

# 2. On COPIE le contenu de ton dossier app local dans l'image
# Note : on remonte d'un cran car le Dockerfile est dans /php
COPY ../app /var/www/html

# 3. On donne les droits à l'utilisateur www-data
RUN chown -R www-data:www-data /var/www/html