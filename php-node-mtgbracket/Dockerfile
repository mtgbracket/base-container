FROM php:7.3.11-apache

# install core extensions.
RUN apt-get update && apt-get install -y \
    libxslt-dev \
    libsodium-dev \
    libzip-dev \
    git \
    g++ \
    zlib1g-dev \
    nano

RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -
RUN apt-get install -y nodejs

RUN docker-php-ext-install xsl
RUN docker-php-ext-install sodium
RUN pecl install zip && \
    docker-php-ext-install zip

RUN pecl install grpc && \
    docker-php-ext-enable grpc

RUN docker-php-ext-install pdo_mysql

RUN pecl install -o -f redis-5.0.2 \
    && rm -rf /tmp/pear \
    && docker-php-ext-enable redis

RUN a2enmod rewrite
RUN a2enmod headers

RUN echo "error_reporting=E_ALL & ~E_DEPRECATED & ~E_NOTICE & ~E_USER_NOTICE" > /usr/local/etc/php/conf.d/mtgbracket.ini