# Create First Docker Image Laravel

## Create Dockerfile

```Dockerfile
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
```

## Build Docker Image

```bash
docker build -t web-app:latest .
```

## Running First Docker Container

```bash
docker run -it \
--rm \
-d \
-p 8000:8000 \
--volume "./.env:/var/www/html/.env" \
--name web-app-1 \
web-app:latest
```

## Check Docker Container

```bash
docker ps
```

## Check Docker Container Logs

```bash
docker logs web-app-1
```

## Access Docker Container

```bash
curl http://localhost:8000
```

## Check Usage of Docker Container

```bash
docker stats web-app-1
```

## Docker login to ghcr.io

```bash
docker login ghcr.io
```

## Docker tag to ghcr.io

```bash
docker tag web-app:latest ghcr.io/username/web-app:latest
```
