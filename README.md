# mapa-registrocivil

Para que funcione el proyecto es importante generar el archivo de entorno .env en base a .envSAMPLE y colocar los pertos que se usarán para los servicios del servidor HTTP, PMA y en su caso la BD.

Es muy importante colocar los password de los usuarios de la BD, su nombre, así como el nombre de la Base de datos.

El proyecto tiene en su configuración el uso de PHP 7.4, se puede cambiar la imagen y poner una relacionada a la versión deseada en el archivo: docker/php/Dockerfile 
Linea 1: FROM php:7.4.33-fpm

Una vez descargado el repo y generado el archivo .env se ejecuta desde la carpeta raíz del proyecto, la instrucción para ejecutar el docker-compose.yml para subir el las imagenes involucradas a memoria con respecto a la configuración indicada.

docker-compose up -d

Para descargar de memoria las imagenes se usa:

docker-compose down

Las imagenes tomarán la carpeta ./app como fuente del código de la aplicación y lo que se encuentra en la carpeta etc es la configuración para los diferentes servicios (nginx, php).

Después de esto se tendrá publicados los servicios en los que se le haya configurado puerto externo en el número de puerto indicado en .env

En el .envSAMPLE se tiene:

La publicación de la aplicación (el puerto es el que hayan definido en .env)
http://localhost:83

La publicación de PMA (phpmyadmin) (el puerto es el que hayan definido en .env), solo se debe de llenar usuario y pwd con respecto a los datos del root o del usuario de la aplicación definido en .env
http://localhost:8083