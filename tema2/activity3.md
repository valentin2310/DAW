# Activity 3

## Ejercicio 1. La UHU (Universidad de Huelva) tiene varios servidores DNS. Consulta a tu servidro DNS por defecto sus direcciones IP al menos 2 de ellas.

Comando: `nslookup .type=ns uhu.es`

Respuesta: 
```
Servidor:  dns.google
Address:  8.8.8.8

Respuesta no autoritativa:
uhu.es  nameserver = dns2.cica.es
uhu.es  nameserver = master.infoblox
uhu.es  nameserver = dns.uhu.es
uhu.es  nameserver = chico.rediris.es
uhu.es  nameserver = sun.rediris.es
uhu.es  nameserver = dns-p.uhu.es
uhu.es  nameserver = dns1.cica.es
uhu.es  nameserver = dns-1.uhu.es
```

Comando: `NSLOOKUP dns-1.uhu.es`

Respusta:
```
Servidor:  dns.google
Address:  8.8.8.8

Respuesta no autoritativa:
Nombre:  dns-1.uhu.es
Address:  150.214.167.1
```

Comando: `NSLOOKUP dns.uhu.es`

Respuesta:
```
Servidor:  dns.google
Address:  8.8.8.8

Respuesta no autoritativa:
Nombre:  dns.uhu.es
Address:  150.214.167.1
```

## Ejercicio 2. ¿Son las respuestas anteriores autoritativas?

Son no autoritativas, porque son servidores recursivos que consultan la información a los servidores DNS autoritativos para encontrar la dirección IP conrrecta.

## Ejercicio 3. Consulta la dirección IP de un servidor de correo de uhu.es.

Comando: `nslookup -type=mx uhu.es dns.uhu.es`

Respuesta:
```
Servidor:  dns.uhu.es
Address:  150.214.167.1

uhu.es  MX preference = 10, mail exchanger = mx04.puc.rediris.es
uhu.es  MX preference = 10, mail exchanger = mx03.puc.rediris.es
```

## Ejercicio 4. ¿Son las respuestas anteriores autoritativas?

Si, porque la respuesta viene del servidor autoritativo del dominio. Además comprobamos que puede existir más de un servidor autoritativo para el mismo dominio.

## Ejercicio 5. Si hay más de un servidor dns autoritativo para el mismo dominio uhu.es, ¿Cómo sabemos cuál es el primario?¿En qué fecha se actualizó por última vez?¿Cúal es la dirección e-mail del administrador?

Comando: `nslookup -type=soa uhu.es dns.uhu.es`

Respuesta:
```
Servidor:  dns.uhu.es
Address:  150.214.167.1

uhu.es
        primary name server = master.infoblox
        responsible mail addr = please_set_email.absolutely.nowhere
        serial  = 2019022075
        refresh = 14400 (4 hours)
        retry   = 7200 (2 hours)
        expire  = 604800 (7 days)
        default TTL = 900 (15 mins)
```

## Ejercicio 6. Comprueba que el DNS inverso está bien configurado para dns-1.uhu.es.

Comando: `nslookup 150.214.167.1`

Respuesta:
```
Servidor:  dns.google
Address:  8.8.8.8

Nombre:  dns-1.uhu.es
Address:  150.214.167.1
```

## Ejercicio 7. Comprueba que el DNS inverso está bien configurado para www.bp.com

Comando: `nslookup bp.com`

Respuesta:
```
Servidor:  dns.google
Address:  8.8.8.8

Respuesta no autoritativa:
Nombre:  bp.com
Address:  54.72.215.189
```

Comando: `nslookup 54.72.215.189`

Respuesta:
```
Servidor:  dns.google
Address:  8.8.8.8

Nombre:  ec2-54-72-215-189.eu-west-1.compute.amazonaws.com
Address:  54.72.215.189
```

## Ejercicio 8. Por defecto, el comando NSLOOKUP devuelve los registrs de tipo A. ¿Qué se obtiene al consultar los registrso NS?.

Se obtienen los servidores autoritativos para un dominio.

Comando: `nslookup`

Respuesta:
```
Servidor predeterminado:  dns.google
Address:  8.8.8.8

> set type=ns
> uhu.es
Servidor:  dns.google
Address:  8.8.8.8

Respuesta no autoritativa:
uhu.es  nameserver = dns1.cica.es
uhu.es  nameserver = dns.uhu.es
uhu.es  nameserver = dns-p.uhu.es
uhu.es  nameserver = sun.rediris.es
uhu.es  nameserver = dns2.cica.es
uhu.es  nameserver = chico.rediris.es
uhu.es  nameserver = dns-1.uhu.es
uhu.es  nameserver = master.infoblox
```

## Ejercicio 9. Consulta el TLD de las páginas de España: "es".

Comando: `nslookup es`

Respuesta:
```
Servidor:  dns.google
Address:  8.8.8.8

Nombre:  es.
```

## Ejercicio 10. ¿Se obtiene alguna respuesta?

No, porque por defecto se buscan registros de tipo A y tipo AAAA. Como "es" no es un FQN, lo lógico es buscar registros NS para saber qué servidores lo resuelven.

Comando: `nslookup -type=ns es`

Respuesta:
```
Servidor:  dns.google
Address:  8.8.8.8

Respuesta no autoritativa:
es  	nameserver = a.nic.es
es  	nameserver = c.nic.es
es  	nameserver = g.nic.es
es  	nameserver = h.nic.es
```

## Ejercicio 11. Consulta las direcciones IP de www.google.com.

Comando: `nslookup google.com`

Respuesta:
```
Servidor:  dns.google
Address:  8.8.8.8

Respuesta no autoritativa:
Nombre:  google.com
Addresses:  2a00:1450:4003:802::200e
      	142.250.185.14
```

## Ejercicio 12. ¿Puede un mismo nombre de dominio traducirse en varias direcciones IP distintas?

Si, por motivos de disponibilidad: si un servidor se avería, los otros pueden mantener el servicio.

## Ejercicio 13. ¿Quién decide a cuál de las direcciones IP se envía una petición?

El solucionador local es quien toma la decisión, ordenando todos los registro A recibidos aleatoriamente y atualizando el primero de la lista. De esa forma se produce un balanceo de carga entre todos los servidores.