FROM php:7.2-fpm
RUN apt-get update
RUN docker-php-ext-install pdo_mysql
RUN sed -i 's/docker-php-\(ext-$ext.ini\)/\1/' /usr/local/bin/docker-php-ext-install



# Install memcache extension

RUN set -x

RUN apt-get update && apt-get install -y --no-install-recommends unzip libssl-dev libpcre3 libpcre3-dev 

RUN cd /tmp 

RUN curl -sSL -o php7.zip https://github.com/websupport-sk/pecl-memcache/archive/php7.zip 

RUN unzip php7 

RUN cd pecl-memcache-php7 

RUN /usr/local/bin/phpize 

RUN ./configure --with-php-config=/usr/local/bin/php-config 

RUN make 

RUN make install 

RUN echo "extension=memcache.so" > /usr/local/etc/php/conf.d/ext-memcache.ini 

RUN rm -rf /tmp/pecl-memcache-php7 php7.zip
ADD php.ini /usr/local/etc/php/
