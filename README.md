TEST DOCKER 
LEONARDO PATZI
ENTORNO DOCKER PHP MYSQL
Configuración inicial
Lo primero será crear una estructura de directorios donde se pondrá tanto el código fuente, como los ficheros de configuración que se usarán. La ruta base que usaré será ./  y a partir de ella se crearán los siguiente directorios:

•	./ Directorio principal donde se almacenara el archivo docker-compose
•	./php: Se almacena el Dockerfile del servidor de aplicaciones y el index.php
•	mysql/data: Directorio donde se almacenarán los datos de MySql

CONTENEDOR PHP_WEB
Para obtener un contenedor con PHP instalado vamos a acceder a Hub Docker donde podemos encontrar multitud de contenedores disponibles para descargar y arrancar. También puedes crearte una cuenta gratuita y subir tus propios contenedores. En nuestro caso vamos a utilizar la última versión disponible en este momento de PHP 7.2.2-Apache.

Para conectarnos a mysql desde php vamos a utilizar el driver pdo_mysql, pero la imagen oficial de Docker no tiene este driver instalado, así que tendremos que crear nuestra propia imagen a partir de la oficial y añadir el driver. Para ello, vamos a la carpeta principal, crearemos un directorio al que llamaremos php y dentro de este un fichero Dockerfile con el siguiente contenido:

FROM php:7.2.2-apache
RUN apt-get update && docker-php-ext-install mysqli pdo pdo_mysql

CONTENEDOR MYSQL

Para el último contenedor, de nuevo seguiremos los mismos pasos que hasta ahora, ir a Hub Docker y buscar en este caso la imagen
oficial de MySql. En este momento la última versión es la 5.7 que es la que usaremos. 
Es interesante darle un vistazo a la documentación ya que se utilizarán algunas de las opciones que se indican a la hora de crear
el contenedor.
