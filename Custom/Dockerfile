# Parte 2
FROM base-phalcon
MAINTAINER Oscar Holmedo <oscarholmedo@gmail.com>

RUN cd /etc/apache2/ && \
	mkdir ssl
COPY ssl /etc/apache2/ssl 
COPY confs/apache2.conf 	/etc/apache2/apache2.conf
COPY confs/000-default.conf /etc/apache2/sites-available/000-default.conf
COPY confs/default-ssl.conf /etc/apache2/sites-available/default-ssl.conf
COPY confs/php.ini 			/etc/php/7.0/cli/php.ini

WORKDIR /var/www/
VOLUME ["/var/www"]

COPY run /usr/local/bin/run
RUN chmod +x /usr/local/bin/run

RUN a2enmod rewrite

EXPOSE 80 443
CMD ["/usr/local/bin/run"]

