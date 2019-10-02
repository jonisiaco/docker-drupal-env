# DRUPAL ENVIROMENT USING DOCKER

## Available versions
- php-fpm 7.3.1
- Mysql 5.7
- Nginx 1.6.1
- phpmyadmin latest

## Installation
- Run `docker-compose up`
- Be aware that NGINX volume is pointing to `./www`. 
- Download Drupal inside this folder `./www`.
- Edit your default virtual host file from `nginx1.6/site.conf` before execute `docker-compose up`(optional)
- Configure `php.ini` from php.ini/site.conf before execute `docker-compose up` (optional)