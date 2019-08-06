FROM php:7.3-apache-buster

# Use the default production configuration
RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

# TODO: xdebug config in this php.ini should be 
# COPY config/php.ini /usr/local/etc/php/

RUN apt-get update && apt-get install -y zlib1g-dev libzip-dev \
#		&& pecl install memcache-3.0.8 \
		&& pecl install xdebug-2.7.2 \
#        && docker-php-ext-enable memcache xdebug \
        && docker-php-ext-enable xdebug \
		&& docker-php-ext-install zip mysqli \
		&& a2enmod rewrite

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

RUN apt-get update && apt-get install -y libxml2-dev \
    && docker-php-ext-install soap
