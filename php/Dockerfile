FROM php:7.2-fpm
RUN apt-get update
RUN docker-php-ext-install pdo_mysql
RUN apt-get install php-memcached
ADD php.ini /usr/local/etc/php/
