FROM php:7.1.11-fpm
ENV TZ=Europe/London

RUN apt-get update \
    && apt-get install -y \
        libicu-dev \
        git \
        libssl-dev \
        libssl-doc \ 
        libsasl2-dev \
        mcrypt \
    && docker-php-ext-install pdo_mysql opcache intl \
    && pecl install apcu && echo "extension=apcu.so" > /usr/local/etc/php/conf.d/apcu.ini \
    && pecl install mongodb && docker-php-ext-enable mongodb \
    #&& echo "extension=mongodb.so" > /usr/local/etc/php/conf.d/mongo.ini
    && ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone \ 
    && printf '[PHP]\ndate.timezone = "Europe/London"\n' > /usr/local/etc/php/conf.d/tzone.ini

COPY php.conf /usr/local/etc/php-fpm.d/zz-php-custom.conf