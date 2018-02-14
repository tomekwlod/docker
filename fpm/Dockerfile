FROM php:7.1.11-fpm
ENV TZ=Europe/London

RUN apt-get update \
    && apt-get install -y \
        libicu-dev \
        git \
        libssl-dev \
        libssl-doc \ 
        libsasl2-dev \
        libxml2-dev \
        mcrypt \
        zlib1g-dev \
        libzip-dev \
        libfreetype6-dev \
		libjpeg62-turbo-dev \
		libmcrypt-dev \
		libpng-dev \
        g++ \
    && docker-php-ext-install pdo_mysql opcache intl ftp simplexml xml \
    && pecl install apcu && echo "extension=apcu.so" > /usr/local/etc/php/conf.d/apcu.ini \
    && docker-php-ext-configure gd \
        --with-freetype-dir=/usr/include/ \
        --with-jpeg-dir=/usr/include/ \
        --with-png-dir=/usr/include/ \
    && docker-php-ext-install gd \
    && pecl install mongodb && docker-php-ext-enable mongodb \
    #&& echo "extension=mongodb.so" > /usr/local/etc/php/conf.d/mongo.ini
    && ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone \ 
    && printf '[PHP]\ndate.timezone = "Europe/London"\n' > /usr/local/etc/php/conf.d/tzone.ini

COPY php.conf /usr/local/etc/php-fpm.d/zz-php-custom.conf