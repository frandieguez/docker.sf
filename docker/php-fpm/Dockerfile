FROM php:fpm

# zlibssl-dev required by mongodb
# lib1g-dev libicu-dev required by intl
# libmcrypt-dev required by mcrypt
RUN apt-get update && \
    apt-get install -y libssl-dev zlib1g-dev libicu-dev g++ libmcrypt-dev && \
    docker-php-ext-install intl && docker-php-ext-configure intl && \
    docker-php-ext-install mcrypt && docker-php-ext-enable mcrypt && \
    docker-php-ext-enable opcache && \
    docker-php-source extract && \
    docker-php-ext-install bcmath && \
    docker-php-ext-install pdo_mysql && \
    docker-php-ext-install zip && \
    pecl install mongodb && docker-php-ext-enable mongodb && \
    pecl install redis && docker-php-ext-enable redis && \
    pecl install xdebug && docker-php-ext-enable xdebug && \
#    pecl install memcached && docker-php-ext-enable memcached && \
    apt-get purge -y g++

RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

