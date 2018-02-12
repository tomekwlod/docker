FROM php:7.1.11-cli

# TO BUILD THIS IMAGE:
    # docker build -t php:7.2.1-cli-intl .

# NOTICE !!! :  USE THIS IMAGE FROM ../../php.sh level

#RUN docker-php-ext-install pdo_mysql  shmop

# https://github.com/docteurklein
RUN apt-get update && apt-get install -y \
        libicu-dev \
        zlib1g-dev \
        libzip-dev \
        git \
    && docker-php-ext-configure intl \
    && docker-php-ext-install pdo_mysql opcache intl \
    && pecl install zip \
    && pecl install mongodb && docker-php-ext-enable mongodb

# disabling short_open_tag
COPY ./php.ini /usr/local/etc/php/php.ini
