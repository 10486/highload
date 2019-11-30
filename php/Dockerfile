FROM php:7.2-fpm
RUN apt-get update
RUN docker-php-ext-install pdo_mysql
RUN apt-get install git
RUN apt-get install build-essential pkg-config make git g++ gcc
RUN apt-get install libmemcached-dev libmsgpack-dev libmsgpackc2
RUN git clone --depth 1 https://github.com/php-memcached-dev/php-memcached.git
RUN cd php-memcached
RUN phpize
RUN ./configure
RUN make
RUN mv modules/ /usr/local/memcached/
ADD php.ini /usr/local/etc/php/
