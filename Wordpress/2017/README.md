
**docker-compose.yml**

    version: '3.8'
    
    services:
      wordpress:
        image: wordpress:4.8.1-php7.1-apache
        container_name: wp-vulnerable
        ports:
          - "8080:80"
        environment:
          WORDPRESS_DB_HOST: db
          WORDPRESS_DB_USER: wordpress
          WORDPRESS_DB_PASSWORD: wordpress
          WORDPRESS_DB_NAME: wordpress
        depends_on:
          - db
    
      db:
        image: mysql:5.7
        container_name: wp-db
        environment:
          MYSQL_DATABASE: wordpress
          MYSQL_USER: wordpress
          MYSQL_PASSWORD: wordpress
          MYSQL_ROOT_PASSWORD: rootpassword
        volumes:
          - db_data:/var/lib/mysql
    
    volumes:
      db_data:

`docker compose up -d`
