# PHP 5.6

FROM php:5-fpm

RUN apt-get update \
    && apt-get install -y zlib1g-dev libicu-dev g++ libmcrypt-dev \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl mbstring pdo_mysql mcrypt mysql

# Default PHP config
RUN if [ -f /usr/local/etc/php/php.ini ]; then rm /usr/local/etc/php/php.ini; fi
COPY ["conf/php.ini", "/usr/local/etc/php/"]

#RUN usermod -u 1000 www-data

EXPOSE 9000