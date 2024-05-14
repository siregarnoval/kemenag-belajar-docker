FROM php:8.3.7-fpm-alpine

WORKDIR /var/www/html
COPY . .

# Install the Composer dependencies
RUN curl -s https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer
RUN composer install

# Install the PHP extensions we need
RUN docker-php-ext-install pdo_mysql bcmath

# Install nodejs and npm
RUN apk add --update nodejs npm
RUN npm install

# Expose the port the app runs on
EXPOSE 8000

# Server Laravel App
CMD php artisan serve --host=0.0.0.0 --port=8000
