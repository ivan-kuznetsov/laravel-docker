FROM php:7.3-fpm

RUN apt-get update && apt-get install -y libmcrypt-dev libpq-dev libicu-dev libmagickwand-dev libjpeg62-turbo-dev libpng-dev libzip-dev zip\
    && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
    && docker-php-ext-configure intl \
    && docker-php-ext-configure gd --with-gd --with-jpeg-dir --with-png-dir --with-zlib-dir \
    && docker-php-ext-install pdo_pgsql pgsql intl zip pdo_mysql gd mysqli\
    && pecl install imagick \
    && docker-php-ext-enable imagick \
    && pecl install redis \
    && docker-php-ext-enable redis

WORKDIR /var/www

#RUN groupadd -r app -g 1000 && useradd -u 1000 -r -g app -m app && chmod 755 /var/www
#
#USER app
