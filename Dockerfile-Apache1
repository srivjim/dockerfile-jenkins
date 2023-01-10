FROM php:8.0-apache
#Instalamos ab en apache
RUN apt-get -qq update && \
	apt-get install -y apache2-utils

#Habilitamos modulo userdir
RUN a2enmod userdir

# Copiar archivo dentro
COPY web/apache1/index.php /var/www/html/index.php

COPY apache.conf /etc/apache2/sites-available/apache.conf
RUN a2dissite 000-default.conf
RUN a2dissite default-ssl.conf
RUN a2ensite apache.conf
CMD ["apachectl", "-D", "FOREGROUND"]
