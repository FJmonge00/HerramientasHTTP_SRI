<img src="/imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Pagina en pruebas

## Lorem Ipsum

```apache
    <VirtualHost *:80>
    	ServerName www.pagina1.org
    
    	ServerAdmin webmaster@localhost
    	DocumentRoot /var/www/pagina1
    
    	ErrorDocument 404 /error/index.html
    
    	ErrorLog ${APACHE_LOG_DIR}/error_pagina1.log
    	CustomLog ${APACHE_LOG_DIR}/access_pagina1.log combined
   	
    #	<Directory /var/www/pagina1/privado>
    #		AuthUserFile "/etc/apache2/claves/passwd.txt"
    #		AuthName "Indique usuario y contraseña"
    #		AuthType Basic
    #		Require valid-user
    #	</Directory>
    	
    	<Directory /var/www/pagina1/privado>
                    AuthUserFile "/etc/apache2/claves/digest.txt"
                    AuthName "asir2"
                    AuthType Digest
    		<RequireAny>
    			Require ip 192.168.3
    			Require valid-user
    		</RequireAny>	
    	</Directory>
    
    
    #	<Directory /var/www/pagina1/privado >
    #	<RequireAll>
    #		Require all granted
    #		Require not ip 192.168.2
    #	</RequireAll>
    #	</Directory>
    	
    #	<Directory /var/www/pagina1/privado >
    #		Order Deny,Allow
    #		Deny from 192.168.2
    #	</Directory>	
    
    </VirtualHost>
```

# LoremIpsum