<img src="/imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Sitios Virtuales

## Teoría

***Antes de empezar un poco de teória NECESARIA...***

**Sitio web:** es un directorio donde tenemos los recursos: html, css, las imágenes, etc. que va a servir nuestro servidor.

*¿Cómo accedemos a los distintos sitios web (Páginas web’s) que puede tener el servidor web?*

**Virtual hosting o sitios virtuales:**
Nos permite acceder a distintas páginas web depositadas en una sola máquina.
    Tenemos:
        **Servidores virtuales por nombre:** Con una sola IP, se accede a los sitios web por nombre o dominio.Ej: www.pagina1.org
        **Servidores virtuales por puerto:** Cada sitio web tiene la misma IP pero un puerto distinto. Ej: 192.168.2.61:8081
        **Servidores virtuales por dirección IP:** Cada sitio web tiene una dirección IP diferente. (Distintas interfaces)

**Directiva DocumentRoot**
Esta directiva indica dónde está la página web que se va mostrar cuando accedamos a ese sitio virtual.
Podemos verlo, en ``/etc/apache2/sites-enabled/000-default.conf``:

![DocumentRoot](/imagenes/apache2/documentRoot.jpg)

*Teoría obtenida de:* [mftienda](https://github.com/mftienda)

## [1.- Configuración sitios virtuales.](./configuracionSitiosVirtuales/)
## [2.- Lorem ipsun.](./apache2/EstructuraFicherosConfiguracion)
## [3.- Loren Ipsum.](./apache2/Directivas)
_________________________________________________
*[Volver atrás...](/README.md)*