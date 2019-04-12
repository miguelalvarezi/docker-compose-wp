FROM php:5.6-apache

COPY config/php.ini /usr/local/etc/php/

RUN apt-get update && apt-get install -y \
		&& apt-get install zlib1g-dev \
		&& pecl install memcache \
		&& pecl install xdebug-2.5.5 \
		&& docker-php-ext-install mysql mysqli \
		&& a2enmod rewrite

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

RUN apt-get update && apt-get install -y libxml2-dev \
    && docker-php-ext-install soap

