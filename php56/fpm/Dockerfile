# PHP 5.6 FPM

FROM php:5-fpm

# Install dependencies and perform cleanup
RUN apt-get update && \
	apt-get install -qy --no-install-recommends zlib1g-dev g++ git

# Install zip
RUN docker-php-ext-install zip

# Install bcmath
RUN docker-php-ext-install bcmath

# Install calendar
RUN docker-php-ext-install calendar

# Install dba
RUN docker-php-ext-install dba

# Install GD
RUN apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng12-dev
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install gd

# Install mbstring
RUN docker-php-ext-install mbstring

# Install mcrypt
RUN apt-get install -y libmcrypt-dev
RUN docker-php-ext-install mcrypt

# Install PDO
# RUN apt-get install -y freetds-dev php5-sybase
RUN docker-php-ext-install pdo_mysql && \
	docker-php-ext-install mysql && \
	docker-php-ext-install mysqli

# RUN docker-php-ext-install pdo_oci
# RUN docker-php-ext-install pdo_odbc
RUN apt-get install -y libpq-dev
RUN docker-php-ext-install pdo_pgsql
RUN apt-get install -y libsqlite3-dev
RUN docker-php-ext-install pdo_sqlite

# Install XSL
RUN apt-get install -y libxslt-dev
RUN docker-php-ext-install xsl

# Install xmlrpc
RUN docker-php-ext-install xmlrpc

# Install intl
RUN apt-get install -y libicu-dev
RUN pecl install intl
RUN docker-php-ext-install intl

# Crear
RUN	apt-get autoremove -yq --purge && \
	rm -rf /tmp/* /var/tmp/* /var/lib/apt/lists/*

# Default PHP config
RUN if [ -f /usr/local/etc/php/php.ini ]; then rm /usr/local/etc/php/php.ini; fi
COPY ["conf/php.ini", "/usr/local/etc/php/"]

WORKDIR /usr/local/apache2/htdocs
RUN usermod -u 501 www-data && \
    usermod -G staff www-data

EXPOSE 9000