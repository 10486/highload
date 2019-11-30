FROM php:7.2-fpm
RUN apt-get update
RUN docker-php-ext-install pdo pdo_mysql mysqli pdo_pgsql
ADD php.ini /usr/local/etc/php/
