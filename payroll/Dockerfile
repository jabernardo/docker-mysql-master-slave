FROM php:8.0-apache

# Copy files to /var/www/html
ADD ./htdocs /var/www/html

# Install vim and common php libs
# RUN echo "deb http://archive.debian.org/debian stretch main" > /etc/apt/sources.list
RUN apt update && apt install vim libz-dev libmcrypt-dev libmemcached-dev libcurl4-openssl-dev pkg-config libssl-dev -y

# Intall memcached from pecl other php ext through `docker-php-ext-install`
RUN pecl install memcached mongodb mcrypt &&\
    docker-php-ext-enable memcached mongodb mcrypt &&\
    docker-php-ext-install mysqli

# Enable php for apache
RUN a2enmod rewrite

# Expose ports
EXPOSE 80