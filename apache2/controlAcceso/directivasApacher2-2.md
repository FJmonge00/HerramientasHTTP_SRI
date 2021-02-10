# Directiva Apache 2.2

>En versiones anteriores de Apache se utilizaban otras directivas para controlar el acceso: Allow, Deny, y Order, están obsoletas y serán quitadas en futuras versiones.

- Order deny,allow hace que por defecto, todos los clientes tengan permitido el acceso

- Order allow,deny hace que por defecto, ningún cliente tenga permitido el acceso

- Allow from permite especificar clientes que tienen permitido el acceso. Ejemplo Allow from 192.168.100.0/24 127.0.0.1

- Deny from permite especificar clientes que no tienen permitido el acceso. Ejemplo Deny from 192.168.2.3 

## Ejemplo 1: Apache 2.2

```apache
<Directory "/var/www">
    Order allow,deny  #Nos fijamos en lo último; deny. Por defecto deniega.
    Allow from all #Aquí podríamos poner quién tiene acceso.
</Directory>
```

## Ejemplo 2: Apache 2.2
 ```apache
<Directory "/var/www">
    Order Deny,Allow  #Nos fijamos en lo último; Allow. Por defecto permite.
    Deny from all
    Allow from example.org
</Directory>
 ```
