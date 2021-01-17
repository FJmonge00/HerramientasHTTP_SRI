<img src="../../imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Instalación Apache2:

``apt install apache2 -y``

*(Opcional) Instalamos documentación de apache2*

``apt install apache2-doc -y``

# Comprobaciones:

## Versión de apache instalada:

``apache2 -v``

## Estado del servicio:

``systemctl status apache2.service``

**ó**

``/etc/init.d/apache2 status``

![estadoServicio](/imagenes/apache2/estadoServicio.jpg)

## Comprobamos desde el navegador:

### Pagina principal de apache2

``firefox 192.168.0.243``

### Documentación local de apache2

``firefox http://192.168.0.243/manual/es/index.html``

![DocumentacionLocal](/imagenes/apache2/documentacionLocal.jpg)

## Procesos:

``ps -aux | grep apache2 | grep -v "grep apache2"``

![procesos](/imagenes/apache2/procesos.jpg)

## Módulos cargados:

``apachectl -M``

![modulos](/imagenes/apache2/modulosCargados.jpg)

## Sitios virtuales:

![sitiosVirtuales](/imagenes/apache2/sitiosVirtuales.jpg)

``apachectl -S``
_________________________________________________
*[Volver atrás...](../README.md)*