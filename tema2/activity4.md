# Activity 4

## Ejercicio 1. Obtén la dirección IP de los siguientes dominios: www.uhu.es, www.us.es, es.wikipedia.org

**www.uhu.es:**

Comando: `dig uhu.es`

Respuesta:
```
; <<>> DiG 9.18.12-0ubuntu0.22.04.3-Ubuntu <<>> uhu.es

;; global options: +cmd

;; Got answer:

;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 45732

;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1



;; OPT PSEUDOSECTION:

; EDNS: version: 0, flags:; udp: 65494

;; QUESTION SECTION:

;uhu.es.				IN	A



;; ANSWER SECTION:

uhu.es.			84003	IN	A	150.214.167.13



;; Query time: 19 msec

;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)

;; WHEN: Sat Jan 27 20:00:23 CET 2024

;; MSG SIZE  rcvd: 51
```


**www.us.es:**

Comando: `dig us.es`

Respuesta:
```
; <<>> DiG 9.18.12-0ubuntu0.22.04.3-Ubuntu <<>> us.es

;; global options: +cmd

;; Got answer:

;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 6929

;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1



;; OPT PSEUDOSECTION:

; EDNS: version: 0, flags:; udp: 65494

;; QUESTION SECTION:

;us.es.				IN	A



;; AUTHORITY SECTION:

us.es.			900	IN	SOA	onix.us.es. redes.us.es. 2024012503 14400 7200 604800 14400



;; Query time: 23 msec

;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)

;; WHEN: Sat Jan 27 20:00:47 CET 2024

;; MSG SIZE  rcvd: 81

```


**www.es.wikipedia.org:**

Comando: `dig es.wikipedia.org`

Respuesta:
```
; <<>> DiG 9.18.12-0ubuntu0.22.04.3-Ubuntu <<>> es.wikipedia.org

;; global options: +cmd

;; Got answer:

;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 55462

;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1



;; OPT PSEUDOSECTION:

; EDNS: version: 0, flags:; udp: 65494

;; QUESTION SECTION:

;es.wikipedia.org.		IN	A



;; ANSWER SECTION:

es.wikipedia.org.	58909	IN	CNAME	dyna.wikimedia.org.

dyna.wikimedia.org.	306	IN	A	185.15.58.224



;; Query time: 15 msec

;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)

;; WHEN: Sat Jan 27 20:01:02 CET 2024

;; MSG SIZE  rcvd: 90

```


## Ejercicio 2. Obtén la dirección y los servidores DNS que corresponden a los siguientes dominios: net, com, us.es, wikipedia.org

**net**

Comando: `dig net NS +noall +answer`

Respuesta:
```
net.			172800	IN	NS	k.gtld-servers.net.

net.			172800	IN	NS	i.gtld-servers.net.

net.			172800	IN	NS	l.gtld-servers.net.

net.			172800	IN	NS	b.gtld-servers.net.

net.			172800	IN	NS	d.gtld-servers.net.

net.			172800	IN	NS	c.gtld-servers.net.

net.			172800	IN	NS	m.gtld-servers.net.

net.			172800	IN	NS	f.gtld-servers.net.

net.			172800	IN	NS	j.gtld-servers.net.

net.			172800	IN	NS	h.gtld-servers.net.

net.			172800	IN	NS	g.gtld-servers.net.

net.			172800	IN	NS	a.gtld-servers.net.

net.			172800	IN	NS	e.gtld-servers.net.

```

**com**

Comando: `dig com NS +noall +answer`

Respuesta:
```
com.			172800	IN	NS	f.gtld-servers.net.

com.			172800	IN	NS	h.gtld-servers.net.

com.			172800	IN	NS	g.gtld-servers.net.

com.			172800	IN	NS	e.gtld-servers.net.

com.			172800	IN	NS	j.gtld-servers.net.

com.			172800	IN	NS	m.gtld-servers.net.

com.			172800	IN	NS	k.gtld-servers.net.

com.			172800	IN	NS	d.gtld-servers.net.

com.			172800	IN	NS	c.gtld-servers.net.

com.			172800	IN	NS	i.gtld-servers.net.

com.			172800	IN	NS	l.gtld-servers.net.

com.			172800	IN	NS	b.gtld-servers.net.

com.			172800	IN	NS	a.gtld-servers.net.

```

**us**

Comando: `dig us NS +noall +answer`

Respuesta:
```
us.			86400	IN	NS	k.cctld.us.

us.			86400	IN	NS	w.cctld.us.

us.			86400	IN	NS	y.cctld.us.

us.			86400	IN	NS	x.cctld.us.

us.			86400	IN	NS	b.cctld.us.

us.			86400	IN	NS	f.cctld.us.

```

**es**

Comando: `dig es NS +noall +answer`

Respuesta:
```
es.			86400	IN	NS	h.nic.es.

es.			86400	IN	NS	a.nic.es.

es.			86400	IN	NS	c.nic.es.

es.			86400	IN	NS	g.nic.es.

```

**wikipedia.org**

Comando: `dig wikipedia.org NS +noall +answer`

Respuesta:
```
wikipedia.org.		86400	IN	NS	ns2.wikimedia.org.

wikipedia.org.		86400	IN	NS	ns0.wikimedia.org.

wikipedia.org.		86400	IN	NS	ns1.wikimedia.org.

```

## Ejercicio 3. Averigua los registrso MX de los siguientes dominios: uhu.es, us.es, wikipedia.org

**uhu.es**

Comando: `dig uhu.es MX +noall +answer`

Respuesta:
```
uhu.es.			86400	IN	MX	10 mx04.puc.rediris.es.

uhu.es.			86400	IN	MX	10 mx03.puc.rediris.es.
```
**us.es**

Comando: `dig us.es MX +noall +answer`

Respuesta:
```
us.es.			14400	IN	MX	10 buzon.us.es.
```
**wikipedia.org**

Comando: `dig wikipedia.org MX +noall +answer`

Respuesta:
```
wikipedia.org.		3600	IN	MX	10 mx1001.wikimedia.org.

wikipedia.org.		3600	IN	MX	10 mx2001.wikimedia.org.
```


## Ejercicio 4. Obtén la dirección IPV6 de www.isc.org

Comando: `dig www.isc.org AAAA`

Respuesta:
```
; <<>> DiG 9.18.12-0ubuntu0.22.04.3-Ubuntu <<>> www.isc.org AAAA

;; global options: +cmd

;; Got answer:

;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 60225

;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1



;; OPT PSEUDOSECTION:

; EDNS: version: 0, flags:; udp: 65494

;; QUESTION SECTION:

;www.isc.org.			IN	AAAA



;; ANSWER SECTION:

www.isc.org.		300	IN	CNAME	isc.map.fastlydns.net.

isc.map.fastlydns.net.	30	IN	AAAA	2a04:4e42:1f::729



;; Query time: 155 msec

;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)

;; WHEN: Sat Jan 27 20:16:11 CET 2024

;; MSG SIZE  rcvd: 103

```

## Ejercicio 5. Muestra los servidores de correo de yahoo.com

Comando: `dig yahoo.com MX +noall +answer`

Respuesa:
```
yahoo.com.		1800	IN	MX	1 mta5.am0.yahoodns.net.

yahoo.com.		1800	IN	MX	1 mta6.am0.yahoodns.net.

yahoo.com.		1800	IN	MX	1 mta7.am0.yahoodns.net.

```

## Ejercicio 6. Muestra la información asociada con la dirección 75.126.153.206

Comando: `dig -x 75.126.153.206`

Respuesta:
```
; <<>> DiG 9.18.12-0ubuntu0.22.04.3-Ubuntu <<>> -x 75.126.153.206

;; global options: +cmd

;; Got answer:

;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 48871

;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1



;; OPT PSEUDOSECTION:

; EDNS: version: 0, flags:; udp: 65494

;; QUESTION SECTION:

;206.153.126.75.in-addr.arpa.	IN	PTR



;; ANSWER SECTION:

206.153.126.75.in-addr.arpa. 3600 IN	PTR	ce.99.7e4b.ip4.static.sl-reverse.com.



;; Query time: 364 msec

;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)

;; WHEN: Sat Jan 27 20:18:58 CET 2024

;; MSG SIZE  rcvd: 106

```

## Ejercicio 7. Muestra la dirección de www.google.es utilizando uno de los servidores DNS de google.com

Comando: `dig @ns1.google.com www.google.com`

Respuesta:
```
; <<>> DiG 9.18.12-0ubuntu0.22.04.3-Ubuntu <<>> @ns1.google.com www.google.com

; (2 servers found)

;; global options: +cmd

;; Got answer:

;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 38303

;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; WARNING: recursion requested but not available



;; OPT PSEUDOSECTION:

; EDNS: version: 0, flags:; udp: 512

;; QUESTION SECTION:

;www.google.com.			IN	A



;; ANSWER SECTION:

www.google.com.		300	IN	A	142.250.184.164



;; Query time: 36 msec

;; SERVER: 216.239.32.10#53(ns1.google.com) (UDP)

;; WHEN: Sat Jan 27 20:20:07 CET 2024

;; MSG SIZE  rcvd: 59

```

## Ejercicio 8. Muestra información sobre el TTL de drive.google.com. Ejecútalo en varias ocasiones y comprueba cómo cambia el valor.

Comando: `dig +nocmd drive.google.com +noall +answer`

Respuesta 1:
```
drive.google.com.	87	IN	A	142.250.184.14

```

Respuesta 2:
```
drive.google.com.	84	IN	A	142.250.184.14

```

Respuesta 3:
```
drive.google.com.	82	IN	A	142.250.184.14

```

## Ejercicio 9. Muestra los registros type NS de redhat.com

Comando: `dig -t NS redhat.com +noall +answer`

Respuesta:
```
redhat.com.		3600	IN	NS	dns3.p01.nsone.net.

redhat.com.		3600	IN	NS	dns4.p01.nsone.net.

redhat.com.		3600	IN	NS	dns1.p02.nsone.net.

redhat.com.		3600	IN	NS	dns2.p02.nsone.net.

redhat.com.		3600	IN	NS	dns1.p01.nsone.net.

redhat.com.		3600	IN	NS	dns2.p01.nsone.net.

```

## Ejercicio 10. Muestar todos los registros de redhat.

Comando: `dig google.com ANY +noall +answer`

Respuesta:
```
google.com.		162	IN	AAAA	2a00:1450:4003:80d::200e

google.com.		280522	IN	NS	ns3.google.com.

google.com.		280522	IN	NS	ns4.google.com.

google.com.		280522	IN	NS	ns1.google.com.

google.com.		280522	IN	NS	ns2.google.com.

google.com.		20	IN	SOA	ns1.google.com. dns-admin.google.com. 601718297 900 900 1800 60

google.com.		119	IN	A	142.250.200.78

google.com.		17273	IN	HTTPS	1 . alpn="h2,h3"

google.com.		120	IN	MX	10 smtp.google.com.

```

## Ejercicio 11. Crea un fichero de texto que contenga los dominios: ubuntu.com, redhat.com

Comando: `nano names.txt`

Fichero names.txt:
```
ubuntu.com
redhat.com
```

## Ejercicio 12. Haz una consulta con dig empleando el fichero anterior.

Comando: `dig -f names.txt +noall +answer`

Respuesta:
```
ubuntu.com.		60	IN	A	185.125.190.20

ubuntu.com.		60	IN	A	185.125.190.21

ubuntu.com.		60	IN	A	185.125.190.29

redhat.com.		3600	IN	A	34.235.198.240

redhat.com.		3600	IN	A	52.200.142.250

```