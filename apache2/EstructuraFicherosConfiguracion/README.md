# Estructura de ficheros de configuración.

**/etc/**

![FicherosApache](/imagenes/apache2/ficherosConfiguracion.png)

**/var/**

![FicherosApache](/imagenes/apache2/ficherosEnVarLogs.png)

## Ficheros principal de Apache2: apache2.conf

``cat /etc/apache2/apache2.conf | grep -v "^#"| grep -v  "^$"``

![FicherosApache](/imagenes/apache2/apache2_conf.jpg)

[Copia Fichero apache2.conf](/apache2/EstructuraFicherosConfiguracion/apache2.conf)
[Copia Sin Comentarios Fichero apache2.conf](/apache2/EstructuraFicherosConfiguracion/apache2.conf.SINCOMENTARIOS)

## Directivas: Directory
Se especifica las opciones de un determinado directorio y de todos sus subdirectorios.
# --> REVISION <--
# --> REVISION <--

## Diferencias entre enabled y available

*Enabled: Activos y visibles*
*Availible: Configurados pero no visibles*

![FicherosApache](/imagenes/apache2/EnableAvailable.png)

**Los sitios,configuraciones y modulos activos son un enlace blando a los ficheros de Available**

### Comandos activar y desactivar:

Configuración --> ``a2enconf`` ``a2disconf``

Modulos --> ``a2enmod`` ``a2dismod``

Sitios Virtuales --> ``a2ensite`` ``a2dissite``

## Los puertos

``/etc/apache2/ports.conf``

![FicherosApache](/imagenes/apache2/ports_conf.jpg)

[Copia Fichero ports.conf](/apache2/EstructuraFicherosConfiguracion/ports.conf)

## Variables de entorno

``/etc/apache2/envvars``

![FicherosApache](/imagenes/apache2/ficheroenvvars.jpg)

[Copia Fichero envvars](/apache2/EstructuraFicherosConfiguracion/envvars)
[Copia Sin Comentarios Fichero envvars](/apache2/EstructuraFicherosConfiguracion/envvars.SINCOMENTARIOS)
## Páginas web

![FicherosApache](/imagenes/apache2/sitiosVirtuales.png)

[Copia Fichero 000-default.conf](/apache2/EstructuraFicherosConfiguracion/000-default.conf)