# WebDav

<img src="/imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

Uno de los aspectos característicos del servidor HTTP Apache es su modularidad.
Apache tiene un sinfín de características adicionales que, si estuvieran siempre incluidas, harían de él un programa demasiado grande y pesado. En lugar de esto, Apache se compila de forma modular y se cargan en memoria sólo los módulos necesarios en cada caso.
Los módulos se guardan en la configuración de apache2 en dos directorios:
- /etc/apache2/mods-available/: Directorio que contiene los módulos disponibles en la instalación actual.
- /etc/apache2/mods-enabled/: Directorio que incluye mediante enlaces simbólicos al directorio anterior, los módulos que se van a cargar en memoria la próxima vez que se inicie Apache.

Cada vez que activemos o desactivemos un módulo hay que reiniciar apache.

Para ver los módulos que tenemos, utilizaremos:
apache2ctl – l  Módulos que se cargan con apache2ctl (núcleo de apache)
/etc/apache2/mods-available   Módulos disponibles. En la mayoría de los casos aparece un .load y .conf.
En los ficheros load, solo aparece la llamada al módulo compilado (so).
En los ficheros .conf, está la configuración del módulo.
Por ejemplo: userdir.conf y userdir.load

apache2ctl –M 🡪 Vemos los módulos activos

3.- Módulo: userdir
Userdir es un módulo de apache que hace posible que todos los usuarios con acceso a un servidor tengan una carpeta llamada public_html en la cual puedan alojar sus páginas y archivos.

__________________________
*[Volver atrás...](/README.md)*


```apache
<VirtualHost *:80>
        ServerName www.pagina1.org
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/pagina1
        DavLockDB /tmp/DavLock
        <Directory /var/www/pagina1/privado>
                dav on
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                AuthUserFile "/etc/apache2/claves/digest.txt"
                AuthName "asir2"
                AuthType Digest
                Require valid-user
        </Directory>
        ErrorLog ${APACHE_LOG_DIR}/error_pagina1.log
        CustomLog ${APACHE_LOG_DIR}/access_pagina1.log combined
</VirtualHost>

# vim: syntax=apache ts=4 somprueba sintaxis
```