FROM php:5.6-apache

COPY config/php.ini /usr/local/etc/php/

RUN apt-get update && apt-get install -y \
		&& apt-get install zlib1g-dev \
		&& pecl install memcache \
		&& pecl install xdebug \
		&& docker-php-ext-install mysql mysqli \
		&& a2enmod rewrite
