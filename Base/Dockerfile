#Parte 1
#Construir con el nombre -t base-phalcon
#o hacer el cambio de nombre en la parte 2
FROM ubuntu:16.04
MAINTAINER Oscar Holmedo <oscarholmedo@gmail.com>

RUN apt-key update && \
	apt-get update && \
    apt-get dist-upgrade -y && \
    apt-get install -y \
    apache2 \
    php7.0 \
	php7.0-dev \
    php7.0-cli \
    libapache2-mod-php7.0 \
    php7.0-gd \
    php7.0-json \
	php-memcached \
    php7.0-ldap \
    php7.0-mbstring \
    php7.0-mysql \
    php7.0-pgsql \
    php7.0-sqlite3 \
    php7.0-xml \
    php7.0-xsl \
    php7.0-zip \
    php7.0-soap \
	vim \
	git 

#instalar phalcon
RUN cd /tmp && \
	curl -s https://packagecloud.io/install/repositories/phalcon/stable/script.deb.sh | bash && \
	apt-get install php7.0-phalcon

#######################################
## Parte 2
#FROM base-phalcon
#MAINTAINER Oscar Holmedo <oscarholmedo@gmail.com>

#RUN cd /etc/apache2/ && \
#	mkdir ssl
#COPY ssl /etc/apache2/ssl 
#COPY confs/apache2.conf 	/etc/apache2/apache2.conf
#COPY confs/000-default.conf /etc/apache2/sites-available/000-default.conf
#COPY confs/default-ssl.conf /etc/apache2/sites-available/default-ssl.conf
#COPY confs/php.ini 			/etc/php/7.0/cli/php.ini

#WORKDIR /var/www/
#VOLUME ["/var/www"]

#COPY run /usr/local/bin/run
#RUN chmod +x /usr/local/bin/run

#RUN a2enmod rewrite

#EXPOSE 80 443
#CMD ["/usr/local/bin/run"]

