FROM php:8.1-apache

RUN a2enmod rewrite

RUN apt-get update && \
    docker-php-ext-install mysqli pdo pdo_mysql

RUN pecl install xdebug && docker-php-ext-enable xdebug 


