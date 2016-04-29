FROM php:7.0-fpm

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        cron \
        libicu-dev \
        libxslt1-dev \
        git-core \
        && cd /tmp/ && git clone https://github.com/derickr/xdebug.git \
        && cd xdebug && phpize && ./configure --enable-xdebug && make \
        && mkdir /usr/lib/php7/ && cp modules/xdebug.so /usr/lib/php7/xdebug.so \
        && touch /usr/local/etc/php/ext-xdebug.ini \
        && rm -r /tmp/xdebug

RUN docker-php-ext-install -j$(nproc) gd pdo_mysql intl xsl zip mcrypt

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-png-dir=/usr/include/

# Configure
COPY ext-xdebug.ini /usr/local/etc/php/conf.d/ext-xdebug.ini

ENV PHP_MEMORY_LIMIT 2G
