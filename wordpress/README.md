# Wordpress docker-compose

This is a simple docker-compose file to run a wordpress site with a mysql database.

## docker-compose.yaml

```yaml
# docker-compose for WordPress
version: "3.8"
services:
  wordpress:
    image: wordpress:latest
    ports:
      - "8000:80"
    environment:
      WORDPRESS_DB_HOST: mysql-db
      WORDPRESS_DB_USER: exampleuser
      WORDPRESS_DB_PASSWORD: examplepass
      WORDPRESS_DB_NAME: exampledb
    volumes:
      - wordpress:/var/www/html
    networks:
      - wordpress-network

  mysql-db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: examplepass
      MYSQL_DATABASE: exampledb
      MYSQL_USER: exampleuser
      MYSQL_PASSWORD: examplepass
    volumes:
      - db:/var/lib/mysql
    networks:
      - wordpress-network

volumes:
  wordpress:
    name: wordpress-data
  db:
    name: wordpress-db

networks:
  wordpress-network:
    name: wordpress-network
    driver: bridge
```

## How to run

1. Create a new directory and create a `docker-compose.yaml` file with the above content.
2. Run `docker-compose up -d` to start the services.
3. Open your browser and go to `http://localhost:8000` to access the WordPress site.

## How to stop

1. Run `docker-compose down` to stop the services.
