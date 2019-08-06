FROM php:7.3-apache-buster

# Use the default production configuration
RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

# TODO: xdebug config in this php.ini should be 
# COPY config/php.ini /usr/local/etc/php/

RUN apt-get update && apt-get install -y zlib1g-dev libzip-dev \
		&& apt-get install -y git \
		&& pecl install xdebug-2.7.2 \
        && docker-php-ext-enable xdebug \
		&& docker-php-ext-install zip mysqli pdo pdo_mysql mbstring

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

ENV COMPOSER_HOME /root/composer

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
    && chmod +x wp-cli.phar \
    && mv wp-cli.phar /usr/local/bin/wp

WORKDIR /var/www/html

EXPOSE 8000
