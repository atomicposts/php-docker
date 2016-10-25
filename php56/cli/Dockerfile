# PHP 5.6 CLI

FROM php:5.6-cli

# Install dependencies and perform cleanup
RUN apt-get update && \
	apt-get install -qy --no-install-recommends zlib1g-dev libicu-dev g++ libmcrypt-dev libpng-dev git && \
	apt-get autoremove -yq --purge && \
	rm -rf /tmp/* /var/tmp/* /var/lib/apt/lists/* && \
	docker-php-ext-install intl && \
	docker-php-ext-install mcrypt && \
	docker-php-ext-install zip && \
	docker-php-ext-install pdo_mysql && \
	docker-php-ext-install mysql && \
	docker-php-ext-install mysqli && \
	docker-php-ext-install gd

# Default PHP config
RUN if [ -f /usr/local/etc/php/php.ini ]; then rm /usr/local/etc/php/php.ini; fi
COPY ["conf/php.ini", "/usr/local/etc/php/"]

# Install Composer && run
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /usr/local/apache2/htdocs
RUN usermod -u 1000 www-data