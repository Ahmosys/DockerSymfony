FROM php:8.0-apache

USER root

RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf

# Update and Dependencies
RUN apt-get update \
    && apt-get install -y --no-install-recommends locales apt-utils git libicu-dev g++ libpng-dev libxml2-dev libzip-dev libonig-dev libxslt-dev npm;

# NPM
RUN npm install npm@latest -g && \
    npm install n -g && \
    n latest

# Symfony CLI
RUN curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh' | bash \
    && apt-get install -y symfony-cli

# French language
RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && \
    echo "fr_FR.UTF-8 UTF-8" >> /etc/locale.gen && \
    locale-gen

# Composer
RUN curl -sSk https://getcomposer.org/installer | php -- --disable-tls && \
    mv composer.phar /usr/local/bin/composer

# PHP Extensions
RUN docker-php-ext-configure intl
RUN docker-php-ext-install pdo pdo_mysql gd opcache intl zip calendar dom mbstring zip gd xsl
RUN pecl install apcu && docker-php-ext-enable apcu

# Permissions
RUN chown -R www-data /var/www

WORKDIR /var/www/

