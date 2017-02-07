#Dockerfile para Phalcon3/Php7/Apache2

El proceso esta en dos partes por comodidad, asi no tiene que tardar todo el proceso de montar el servidor base cada vez que se requiera  hacer ajustes en los archivos de configuracion 
<br>
##1.- Crear el contenedor base. Instalar apache, php y phalcon.
<p>descargar los archivos y compilar la carpeta /Base </p>

<pre>
$ cd Base 
$ docker build -t base-phalcon . 
</pre>


##2.- Crear el contenedor dinamico para personalizar los archivos de configuracion (considerando que se uso el nombre "base-phalcon" en el build anterior)
<pre>
$ cd Custom 
$ docker build -t custom-phalcon . 
</pre>

###Archivos de configuracion
confs/php.ini -> /etc/php/7.0/cli/php.ini
confs/apache2.conf ->	/etc/apache2/apache2.conf
confs/000-default.conf -> /etc/apache2/sites-available/000-default.conf
confs/default-ssl.conf -> /etc/apache2/sites-available/default-ssl.conf

###Carpeta para certificados ssl
ssl -> /etc/apache2/ssl 

###Volumenes
/var/www/ 
/var/log/apache2/

###Puertos
80 443


##Ejecutar el contenedor
<pre>
$ docker run -d -p 8080:80  \ 
  -v /local/www/:/var/www/ \
  -v /local/log/:/var/log/apache2/ \
  custom-phalcon
</pre>

##Entrar en el contendor
<pre>docker run -it custom-phalcon bash</pre>

#Alternativa
Compila en un solo paso con el contenido del Custom/Dockerfile-OneStep
