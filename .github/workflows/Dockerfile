FROM php:8.1-slim AS builder

WORKDIR /app

COPY composer.json composer.lock package.json npm-shrinkwrap.json .

RUN composer install --no-interaction --optimize
RUN npm install --production

FROM php:8.1-apache

RUN docker-php-ext-install mysqli

EXPOSE 80

CMD ["apache2", "-f", "/etc/apache2/sites-available/000-default.conf"]
