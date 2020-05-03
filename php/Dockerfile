FROM php:fpm
RUN apt-get update \
    && apt-get -y install libzip-dev \
    && apt-get install -y zlib1g-dev \
    && apt-get -y install unzip \
    && docker-php-ext-install zip
RUN docker-php-ext-install zip pdo_mysql

COPY --from=composer /usr/bin/composer /usr/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin
RUN composer global require "laravel/installer"
