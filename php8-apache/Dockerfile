FROM php:8.0.1-apache-buster

RUN docker-php-ext-install pdo pdo_mysql bcmath opcache 

RUN apt-get update && apt-get install -y \
    zlib1g-dev \
    libzip-dev nodejs npm
RUN docker-php-ext-install zip 

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN a2enmod rewrite

COPY vhost.conf /etc/apache2/sites-available
RUN a2ensite vhost.conf
