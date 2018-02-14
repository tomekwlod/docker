FROM php:7.1.11-cli

# TO BUILD THIS IMAGE:
    # docker build -t php:7.2.1-cli-intl .

# NOTICE !!! :  USE THIS IMAGE FROM ../../php.sh level

#RUN docker-php-ext-install pdo_mysql  shmop

# https://github.com/docteurklein
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
    # && pecl install zip \
    # && pecl install apcu && echo "extension=apcu.so" > /usr/local/etc/php/conf.d/apcu.ini \
    && pecl install mongodb && docker-php-ext-enable mongodb
    #&& echo "extension=mongodb.so" > /usr/local/etc/php/conf.d/mongo.ini
    # && ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone \ 
    # && printf '[PHP]\ndate.timezone = "Europe/London"\n' > /usr/local/etc/php/conf.d/tzone.ini
# disabling short_open_tag

COPY ./php.ini /usr/local/etc/php/php.ini
