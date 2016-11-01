# Apache

FROM httpd:2.4
RUN mkdir -p /usr/local/apache2/conf/vhosts
COPY conf/httpd.conf /usr/local/apache2/conf/httpd.conf

WORKDIR /usr/local/apache2/htdocs
RUN usermod -u 501 www-data && \
    usermod -G staff www-data

EXPOSE 80 443