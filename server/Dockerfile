FROM php:7.4-apache

WORKDIR "/var/www/html"

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        unzip \
        wget \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd gettext mysqli pdo_mysql

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

RUN a2enmod rewrite
RUN cd /var/www/html && wget https://github.com/alextselegidis/easyappointments/releases/download/1.4.2/easyappointments-1.4.2.zip && unzip -x easyappointments-1.4.2.zip && rm easyappointments-1.4.2.zip && chmod 777 -R storage

