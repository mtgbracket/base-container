FROM php:7.3.11-apache

# install core extensions.
RUN apt-get update && apt-get install -y \
    libxslt-dev \
    libsodium-dev \
    libzip-dev \
    git \
	nodejs

RUN docker-php-ext-install xsl
RUN docker-php-ext-install sodium
RUN pecl install zip && \
    docker-php-ext-install zip

RUN docker-php-ext-install pdo_mysql

RUN pecl install -o -f redis-5.0.2 \
    && rm -rf /tmp/pear \
    && docker-php-ext-enable redis

RUN a2enmod rewrite
RUN a2enmod headers
