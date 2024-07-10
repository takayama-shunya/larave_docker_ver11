FROM php:8.3-fpm

# COPY php.ini
COPY ./Docker/php/php.ini /usr/local/etc/php/php.ini

# install Node.js
# COPY --from=node:14.18.2 /usr/local/bin /usr/local/bin
# COPY --from=node:14.18.2 /usr/local/lib /usr/local/lib

RUN apt-get update \
    && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libzip-dev \
        zlib1g-dev \
        unzip \
        vim \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install \
        gd \
        zip \
        pdo_mysql

# Composer install
COPY --from=composer:2.7 /usr/bin/composer /usr/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1

ENV COMPOSER_HOME /composer

ENV PATH $PATH:/composer/vendor/bin


