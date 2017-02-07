#Dockerfile para Phalcon3/Php7/Apache2

El proceso esta en dos partes por comodidad, asi no tiene que tardar todo el proceso de montar el servidor base cada vez que se requiera  hacer ajustes en los archivos de configuracion 
<br>
1.- Crear el contenedor base. Instalar apache, php y phalcon.
<p>descargar los archivos y compilar la carpeta /Base </p>

<pre>
cd Base 
<br>
docker build -t oscarholmedo/php7-apache2-phalcon3 . 
</pre>


2.- Crear el contenedor dinamico para personalizar los archivos de configuracion
<pre>
cd Custom 
<br>
docker build -t phalcon . 
</pre>



<br>
confs/php.ini -> /etc/php/7.0/cli/php.ini
<br>
confs/apache2.conf ->	/etc/apache2/apache2.conf
<br>
confs/000-default.conf -> /etc/apache2/sites-available/000-default.conf
<br>
confs/default-ssl.conf -> /etc/apache2/sites-available/default-ssl.conf

##Carpeta para certificados ssl
ssl -> /etc/apache2/ssl 


##Ejecutar el contenedor
<pre>docker run -d -p 8080:80  -v /local/www/:/var/www/ -v /local/log/:/var/log/apache2/ oscarholmedo/php7-apache2-phalcon3</pre>

<pre>docker run -it php7-apache2-phalcon3 bash</pre>
