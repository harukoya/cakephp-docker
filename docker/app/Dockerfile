FROM php:8.1.4-fpm-alpine
COPY php.ini /usr/local/etc/php/

COPY --from=composer /usr/bin/composer /usr/bin/composer
ENV PATH $PATH:/var/www/vendor/bin

RUN apk --no-cache update && \
    apk --no-cache upgrade && \
    apk --no-cache add icu-dev zlib-dev libzip-dev mariadb mariadb-client vim && \
    docker-php-ext-configure intl && \
    docker-php-ext-install intl zip pdo pdo_mysql mysqli && \
    docker-php-ext-enable intl

WORKDIR /var/www
