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