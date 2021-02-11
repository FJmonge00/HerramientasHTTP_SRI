# WebDav

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