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

### Comprobar el funcionamiento de PHP (Opcional)

## 4. Crear un host virtual

Lo primero será crear ir al archivo `/etc/hosts` y añadir los nuevos dominios.

Para ello ejecutamos el siguiente comando:

`sudo nano /etc/hosts`

Dentro del fichero añadimos nuestros nuevos dominios.

![Imagen con el resultado del comando anterior](./img/7.png)

A continuación vamos a crear un archivo de configuración en `/etc/apache2/sites-available`, por ejemplo: `WordPress.conf`.

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

## 5. Configurar e instalar WordPress

