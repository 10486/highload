FROM php:7.2-fpm
RUN apt-get update
RUN docker-php-ext-install pdo_mysql
RUN apt-get install -y 
        libmemcached11 \
        libmemcachedutil2 \
        libmemcached-dev \
        libz-dev \
        git \
    && cd /root \
    && git clone -b php7 https://github.com/php-memcached-dev/php-memcached \
    && cd php-memcached \
    && phpize \
    && ./configure \
    && make \
    && make install \
    && cd .. \
    && rm -rf  php-memcached \
    && echo extension=memcached.so >> /usr/local/etc/php/conf.d/memcached.ini \
    && apt-get remove -y build-essential libmemcached-dev libz-dev \
    && apt-get remove -y libmemcached-dev libz-dev \
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/* \
    && apt-get clean
ADD php.ini /usr/local/etc/php/
