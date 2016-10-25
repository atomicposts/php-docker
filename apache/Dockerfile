# Apache

FROM httpd:2.4
RUN mkdir -p /usr/local/apache2/conf/vhosts
COPY conf/httpd.conf /usr/local/apache2/conf/httpd.conf

WORKDIR /usr/local/apache2/htdocs
RUN usermod -u 1000 www-data

EXPOSE 80 443