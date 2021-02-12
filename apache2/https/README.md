<img src="/imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Acceso Seguro SSL/TLS (HTTPs)

Autoridades de certificación gratuitas:
**Let’s Encrypt**: Tiene un cliente  llamado Certbot que automatiza todo el ciclo de vida de la gestión de certificados: obtención, renovación, revocación, instalación en el servidor web, etc.

**CAcert**: es Free digital certificates for everyone y es que la utilización de certificados emitidos por CA comerciales no es posible para todos los sitios de Internet debido a su coste, lo que limita su uso a transacciones económicas o sitios con datos relevantes. CAcert es una organización sin ánimo de lucro que mantiene una infraestructura equivalente a una CA comercial aunque con ciertas limitaciones.

## Objetivo:

Necesitamos:
1. Generar un certificado TLS/SSL, formato 509, que indique que el servidor web es un servidor legítimo.
Ese certificado llevará :
- Entidad de nuestro sitio web.
- Clave pública de nuestro sitio web.
- Firma de una autoridad de certificación.

2. Una clave privada, para establecer una comunicación cliente-servidor encriptada.
3. Instalarlo en el servidor web.

Para generar un certificado TLS/SSL vamos a utilizar la herramienta OpenSSL.

## Activar modulo SSL

```bash
#Módulo para la autenticación básica
ls -l --color /etc/apache2/mods-enabled/ssl.load
```

*Sí está desactivado...*

```bash
a2enmod ssl
systemctl restart apache2 
```

## Generar pareja de claves (OpenSSL)

### Instalar OpenSSL

```bash
apt policy openssl
#Si no esta instalado..
apt install openssl
```

*Certificados y claves actuales*
```bash
ls /etc/ssl
```

**Generar certificado firmado y claves en 1 paso**

```bash
openssl req -x509 -nodes -days 1095 -newkey rsa:2048 -keyout /etc/ssl/pagina1.key -out /etc/ssl/pagina1.crt
```
ó

**Para hacerlo en 3 paso**

```bash
cd /etc/ssl
```

*Generar clave*
![crearUsuarios](../../imagenes/apache2/https0.jpg)

```bash
ls /etc/ssl
```

*Generar Certificado*
![crearUsuarios](../../imagenes/apache2/https1.jpg)

*Firmar Certificado*
![crearUsuarios](../../imagenes/apache2/https4.jpg)

## Configuración del sitio virtual

cp /etc/apache2/sites-available/pagina1.conf /etc/apache2/sites-available/pagina1-ssl.conf

*Para activar Https esta es la configuración principal...*

```apache
SSLEngine on
SSLCertificateKeyFile /etc/ssl/pagina1.key
SSLCertificateFile /etc/ssl/pagina1.crt
```

![crearUsuarios](../../imagenes/apache2/opcionesHttps.jpg)

*Configuración*
# DA ERROR
```apache
<VirtualHost *:443>
	ServerName www.pagina1.org
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/pagina1
	SSLEngine on
	SSLCertificateFile /etc/ssl/pagina1.key
	SSLCertificateKeyFile /etc/ssl/pagina1.crt
	ErrorLog ${APACHE_LOG_DIR}/error_pagina1-ssl.log
	CustomLog ${APACHE_LOG_DIR}/access_pagina1-ssl.log combined
</VirtualHost>

# vim: syntax=apache ts=4 somprueba sintaxis
```


### Activar sitio virtual apache2.conf

```bash
a2ensite pagina1-ssl.conf
```

ó

### Directamente en el sitio virtual

```bash
vi /etc/apache2/pagina1.conf
```

*Reiniciamos el servicio*

```bash
apache2ctl -t
systemctl restart apache2 
systemctl status apache2 
```

## Configuraciones desde .htaccess

### Crear htaccess

```bash
cd /var/www/pagina1/
touch /var/www/pagina1/.htaccess
chown -R www-data:www-data /var/www/pagina1/
ls -lRa --color /var/www/pagina1/
```

### Indexes

#### Permitir Indexes

*renombramos el index.html para que no lo lea por defecto*

```bash
mv /var/www/pagina1/index.html /var/www/pagina1/index.tmp
echo "Options Indexes" > /var/www/pagina1/.htaccess
chown -R www-data:www-data /var/www/pagina1/
ls -l /var/www/pagina1/index.*
firefox http://www.pagina1.org/
```
*No es necesario recargar el servicio los cambios son desde el cliente*

#### Denegar Indexes

```bash
echo "Options -Indexes" > /var/www/pagina1/.htaccess
chown -R www-data:www-data /var/www/pagina1/
firefox http://www.pagina1.org/
```

*No es necesario recargar el servicio los cambios son desde el cliente*

***Comprobaciones:** *debe devolver un error 403 ó Forbidden*

### Cliente modifica el sitio virtual: *Activa la autenticación*


```bash
echo 'AuthUserFile "/etc/apache2/claves/passwd.txt"' > /var/www/pagina1/.htaccess
echo 'AuthName "Indroduce las claves:"' >> /var/www/pagina1/.htaccess
echo 'AuthType Basic' >> /var/www/pagina1/.htaccess
echo 'Require valid-user' >> /var/www/pagina1/.htaccess
firefox http://www.pagina1.org/
```
*No es necesario recargar el servicio los cambios son desde el cliente*

![crearUsuarios](../../imagenes/apache2/configDesdeClienteAcceso.jpg)

*ES NECESARIO CREAR LOS USUARIOS EN CASO DE QUE NO EXISTA*

```bash
mkdir /etc/apache2/claves/
htpasswd -c /etc/apache2/claves/passwd.txt usuario01 # Opción -c SOLO PARA CREAR EL FICHERO 1ª Vez
htpasswd /etc/apache2/claves/passwd.txt usuario02
```

*Si no está instalado htpasswd...*

```bash
apt-get install apache2-utils
```

### Cliente modifica el sitio virtual: Deniega los archivos .tmp

![crearUsuarios](../../imagenes/apache2/bloqueTMPCliente.jpg)
__________________________
*[Volver atrás...](/README.md)*