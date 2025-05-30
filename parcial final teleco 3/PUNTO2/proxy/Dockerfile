FROM php:7.4-apache

RUN apt-get update && apt-get install -y vim && rm -rf /var/lib/apt/lists/*

# Habilitar módulos proxy necesarios
RUN a2enmod proxy proxy_http ssl rewrite

RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf

COPY certificado.crt /etc/ssl/certs/certificado.crt
COPY privada.key /etc/ssl/private/privada.key

COPY my-httpd-vhosts.conf /etc/apache2/sites-available/my-ssl.conf

RUN a2dissite 000-default default-ssl && a2ensite my-ssl
