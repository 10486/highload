FROM php:7.2-fpm
RUN apt-get update
RUN docker-php-ext-install pdo_mysql
RUN apt-get install -y php-memcached 
RUN apt-get install -y --no-install-recommends \
    curl \
    libmemcached-dev \
    libz-dev \
    libpq-dev \
    libjpeg-dev \
    libpng-dev \
    libfreetype6-dev \
    libicu-dev \
    libssl-dev \
    libmcrypt-dev && \
    docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr && \
    docker-php-ext-install gd mysqli opcache intl

    

 # Install Memcached
RUN curl -L -o /tmp/memcached.tar.gz "https://github.com/php-memcached-dev/php-memcached/archive/php7.tar.gz"
RUN mkdir -p memcached
RUN tar -C memcached -zxvf /tmp/memcached.tar.gz --strip 1 && \
( \
    cd memcached && \
    phpize && \
    ./configure && \
    make -j$(nproc) && \
    make install \
)
RUN rm -r memcached
RUN rm /tmp/memcached.tar.gz
RUN docker-php-ext-enable memcached
ADD php.ini /usr/local/etc/php/
