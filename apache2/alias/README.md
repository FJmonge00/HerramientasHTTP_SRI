<img src="/imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Trabajando con alias

Las directiva Alias nos permite que el servidor sirva ficheros desde cualquier ubicación del sistema de archivo aunque este fuera del directorio indicado en el DocumentRoot.

Ej: Alias "/imagenes" "/ftp/publico/imagenes"

## Preparamos el los datos

```bash
mkdir /home/usuario/datos
wget https://i.blogs.es/5efe2c/cap_001/450_1000.jpg
chown -R usuario:usuario /home/usuario/datos
ls -l /home/usuario/datos
```

## Configuracion del Sitio Virtual

*Añadir...*

```bash
Alias "/datos" "/home/usuario/datos"
<Directory "/home/usuario/datos">
    Require all granted
</Directory>
```

```bash
vi /etc/apache2/sites-available/pagina1.conf
```

_________________________________________________
*[Volver atrás...](/README.md)*