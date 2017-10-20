######
# See: https://hub.docker.com/_/php/
######

FROM php:7.1.10-fpm
MAINTAINER Sergi Ortega <@sortegam>

######
# You can install php extensions using docker-php-ext-install
######

RUN apt-get update && apt-get install -y \
    libmcrypt-dev \
    libjpeg62-turbo-dev \
    libpcre3-dev \
    libpng12-dev \
    libfreetype6-dev \
    libxml2-dev \
    libicu-dev \
    mysql-client \
    wget \
    unzip \
  && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
  && docker-php-ext-install iconv intl mcrypt pdo pdo_mysql mbstring soap gd zip

RUN docker-php-source extract \
  && if [ -d "/usr/src/php/ext/mysql" ]; then docker-php-ext-install mysql; fi \
  && if [ -d "/usr/src/php/ext/opcache" ]; then docker-php-ext-install opcache; fi \
  && docker-php-source delete
