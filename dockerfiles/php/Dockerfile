FROM php:5.6-cli

COPY config/php.ini /usr/local/etc/php/

RUN apt-get update && apt-get install -y zlib1g-dev \
		&& apt-get install -y git \
		&& pecl install xdebug \
		&& docker-php-ext-install zip mysql mysqli pdo pdo_mysql mbstring

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng12-dev \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

ENV COMPOSER_HOME /root/composer

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
    && mv wp-cli.phar /usr/local/bin/wp \
    && chmod +x /usr/local/bin/wp

WORKDIR /var/www/html

EXPOSE 8000
