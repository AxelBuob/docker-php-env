# docker-php-env
Docker images:
    - php:7.4-fpm
    - mysql:5.7
    - nginx:alpine
    - composer:latest
    - adminer

Php exentions:
    - pdo_mysql 
    - mbstring 
    - exif 
    - pcntl 
    - bcmath 
    - gd

Linux packages:
    - git 
    - curl 
    - libpng-dev 
    - libonig-dev 
    - libxml2-dev 
    - zip 
    - unzip

DB_NAME = demo
DB_USER = demo
DB_PASSWORD = password
DB_ROOT_PASSWORD = password

Instructions:
1. Run docker-compose up
2. Go to localhost:8000 or localhost:8080 for adminer
3. Run docker-compose exec app composer <command> to install a package
