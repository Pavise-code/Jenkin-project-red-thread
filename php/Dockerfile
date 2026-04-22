FROM php:8.1-fpm

RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli

WORKDIR /var/www/html

# On enlève les "../" car on va changer le contexte de build
COPY ./app /var/www/html

RUN chown -R www-data:www-data /var/www/html