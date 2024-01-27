# Práctica Servidores web

Vamos a instalar un servidor web apache. Usaremos dos dominios mediante el archivo hosts: centro.intranet y departamentos.centro.intranet.

El primero servirá el contenido mediante wordpress y el segundo una aplicación en python.

## 1. Instalar y configurar el servidor web Apache

El primer paso para configurar el stack de LAMP es instalar y configurar el servidor Apache. En primer lugar, tenemos que actualizar la lista de paquetes de tu sistema y actualizar los paquetes a la versión más reciente.

`sudo apt update`

Ahora para instalar Apache2 ejecuta el siguiente comando:

`sudo apt install apache2`

Una vez que la instalación se complete, deberá ajustar la configuración de su firewall para permitir tráfico HTTP y HTTPS. Para enumerar todos los perfiles de aplicaciones de UFW disponibles, puede ejecutar lo siguiente:

`sudo ufw app list`

Resultado del comando:

![Imagen con el resultado del comando anterior](./img/3.png)

Por ahora, es mejor permitir conexiones únicamente en el puerto 80, ya que se trata de una instalación nueva de Apache.

Para permitir tráfico únicamente en el puerto 80 utilice el perfil Apache:

`sudo ufw allow in "Apache"`

Para verificar el cambio puede usar: 

`sudo ufw status`

![Imagen con el resultado del comando anterior](./img/5.png)

## 2. Instalar MySQL

Ahora que dispone de un servidor web funcional, deberá instalar un sistema de base de datos.
Use el siguiente comando para instalar este software:

`sudo apt install mysqli-server`

![Imagen con el resultado del comando anterior](./img/8.png)

Podremos comprobar si funciona usando el comando `mysql`

![Imagen con el resultado del comando anterior](./img/9.png)

## 3. Instalar PHP

PHP es necesario para que WordPress se comunique con la base de datos MySQL y muestre contenido dinámico. También necesitarás instalar extensiones PHP adicionales para WordPress.

Ejecuta el siguiente comando para instalar PHP y las extensiones de PHP a la vez:

`sudo apt install php libapache2-mod-php php-mysql`

![Imagen con el resultado del comando anterior](./img/10.png)

Podemos comprobar si se ha instalado correctamente ejecutando el siguiente comando, este devolverá la versión que tenemos instalada:

`php -v`

![Imagen con el resultado del comando anterior](./img/11.png)

## 4. Crear un host virtual

Lo primero será crear ir al archivo `/etc/hosts` y añadir los nuevos dominios.

Para ello ejecutamos el siguiente comando:

`sudo nano /etc/hosts`

Dentro del fichero añadimos nuestros nuevos dominios.

![Imagen con el resultado del comando anterior](./img/7.png)

## 5. Prepara WordPress

Vamos a crear un archivo de configuración en `/etc/apache2/sites-available`, por ejemplo: `WordPress.conf`.

Para ello podemos usar el siguiente comando:

`sudo nano /etc/apache2/sites-available/WordPress.conf`

Dentro del fichero añadimos las siguientes líneas: 

![Imagen con el resultado del comando anterior](./img/13.png)

Ahora vamos a crear un directorio para nuestro WordPress.

`sudo mkdir /var/www/wordpress`

Ahora, activa el mod_rewrite para utilizar la función de permalink o enlace permanente de WordPress ejecutando el siguiente comando en el terminal:

`sudo a2enmod rewrite`

Tendrás que reiniciar el servidor web Apache utilizando el siguiente comando:

`systemctl restart apache2`

Ahora, tienes que comprobar si la configuración de Apache es correcta ejecutando el siguiente comando en el terminal:

`sudo apachectl configtest`

![Imagen con el resultado del comando anterior](./img/14.png)

## 6. Configurar e intalar WordPress

Vamos a configurar WordPress a través del navegador, para ello primero intala el paquete wget.

`sudo apt install wget -y`

![Imagen con el resultado del comando anterior](./img/15.png)

A continuación, utiliza el comando wget seguido del enlace de descarga de WordPress:

`wget https://wordpress.org/latest.zip`

![Imagen con el resultado del comando anterior](./img/16.png)

Una vez que hayas descargado el archivo comprimido, instala la utilidad de descompresión utilizando estos comandos:

`sudo apt install unzip -y`

![Imagen con el resultado del comando anterior](./img/17.png)

Ahora tendrás que mover el archivo al directorio correcto antes de descomprimirlo. Utiliza el comando:

`mv latest.zip /var/www/wordpress`

A continuación, navega hasta el directorio y descomprime el archivo utilizando estos comandos:

`cd /var/www/wordpress`
`unzip latest.zip`

Después, utiliza el siguiente comando para mover el directorio:

`mv -f wordpress/* ./`

Una vez hecho esto, reinicia Apache utilizando estos comandos:

`sudo systemctl restart apache2
sudo chown -R www-data:www-data /var/www/`

Ahora vamos a activar nuestro WordPress, para ello usamos el siguiente comando seguido del nombre de configuración del fichero de configuración sin la extension .conf:

`sudo a2ensite WordPress`

Reiniciamos apache y comprobamos si está todo correcto.

`systemctl reload apache2`

`sudo apache2ctl configtest`

![Imagen con el resultado del comando anterior](./img/21.png)

Termina de configurar WordPress a través de un navegador web. Abre un navegador web y escribe la dirección IP del servidor.

Primero nos pedirá que seleccionemos el idioma.
Luego completamos el formulario para conectar wordpress con la base de datos.
En usuario colocamos el que creamos en la base de datos y la base de datos también la que creamos anteriormente.

![Imagen con el resultado del comando anterior](./img/22.png)

Empezamos la instalación.

![Imagen con el resultado del comando anterior](./img/23.png)

Configuramos nuestro sitio web y por último le damos a intalar WordPress.

![Imagen con el resultado del comando anterior](./img/24.png)

Iniciamos sesión en WordPress con el usuario que creamos en el formulario anterior.

![Imagen con el resultado del comando anterior](./img/25.png)

Y eso es todo, ya tenemos WordPress.

![Imagen con el resultado del comando anterior](./img/26.png)

## 7. Servidor Web con Python

En principio, necesitamos hacer que Apache, incorpore un soporte para servir archivos Python. Para ello, necesitaremos habilitarle un módulo, que brinde este soporte.

Para habilitar mod_wsgi en Apache, basta con instalar el paquete libapache2-mod-wsgi:

`sudo apt-get install libapache2-mod-wsgi-py3`

![Imagen con el resultado del comando anterior](./img/servidor_python/8.png)

Ahora vamos a crear la estructura de carpetas de nuestro proyecto.

Primero creamos nuestro directorio.

Dentro de este directorio, vamos a dividir su arquitectura en dos partes:

1. Destinada al almacenaje de nuestra aplicación Python pura (será un directorio privado, no servido).
2. Destinada a servir la aplicación (directorio público servido) en el cuál solo almacenaremos archivos estáticos.

![Imagen con el resultado del comando anterior](./img/servidor_python/2.png)

Aprovecharemos este paso, para crear una carpeta, destinada a almacenar los logs de errores y accesos a nuestra Web App:

![Imagen con el resultado del comando anterior](./img/servidor_python/3.png)

Vamos a crear un controlador para la aplicación, que estará almacenado en nuestro directorio mypythonapp.

`echo '# -*- coding: utf-8 -*-' > mypythonapp/controller.py`

![Imagen con el resultado del comando anterior](./img/servidor_python/4.png)

Este archivo controller.py actuará como un pseudo front controller, siendo el encargado de manejar todas las peticiones del usuario, haciendo la llamada a los módulos correspondientes según la URI solicitada.

Dentro del archivo vamos a introducir el siguiente cógido:

`

    def application(environ, start_response):

    # Genero la salida HTML a mostrar al usuario

    output = u"<p>Bienvenido a mi <b>PythonApp</b>!!!</p>".encode('utf-8')



    # Inicio una respuesta al navegador

    start_response('200 OK', [('Content-Type', 'text/html; charset=utf-8')])



    # Retorno el contenido HTML como bytes

    return [output]

`

![Imagen con el resultado del comando anterior](./img/servidor_python/5.png)

Ahora vamos a configurar nuestro VirtualHost, para ello nos vamos a la configuración de nuestro sitio web:

`sudo nano /etc/apache2/sites-available/servidor-python.conf`

Dentro del archivo escribimos el siguiente codigo.

Mientras que el DocumentRoot de nuestro sitio Web, será la carpeta pública, public_html, una variable del VirtualHost, será la encargada de redirigir todas las peticiones públicas del usuario, hacia nuestro front controller. Y la variable que se encargue de esto, será el alias WSGIScriptAlias:

![Imagen con el resultado del comando anterior](./img/servidor_python/7.png)

Ahora solo queda habilitar el sitio web, recargar apache y comprobar que todo este correcto.

![Imagen con el resultado del comando anterior](./img/servidor_python/10.png)

Vamos a comprobar nuestro sitio web.

![Imagen con el resultado del comando anterior](./img/servidor_python/servidor_funcionando.png)

### Añadir autenticación de usuario (opcional)

Para ello vamos a crear un archivo .htpasswd para almacenar el usuario y contraseña.

`htpasswd -c /home/valentinac/servidor-python/.htpasswd usuario`

Luego vamos a cambiar el archivo de configuración de nuestro sitio web, vamos a modificarlo para que quede de la siguiente forma:

![Imagen con el resultado del comando anterior](./img/servidor_python/validacion_usuario.png)

Recargamos apache y probamos nuestro sitio web de nuevo.

![Imagen con el resultado del comando anterior](./img/servidor_python/servidor_funcionando.png)