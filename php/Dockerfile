FROM php:7.2-fpm
RUN apt-get update
RUN set -ex 
RUN apk --no-cache add \
postgresql-dev
RUN docker-php-ext-install pdo mysqli pdo_pgsql
ADD php.ini /usr/local/etc/php/
