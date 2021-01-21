<img src="/imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Configuración de Sitios Virutales (Básica)

## Parámetros sitioVirtual.conf

![ConfigiracionBasica](../../../imagenes/apache2/ConfigiracionBasica.png)

Cualquier **IP** del Servidor puerto **80**:

``ServerName www.pagina1.org``

**Dominio** del sitio virtual:

``ServerAdmin webmaster@localhost``

**Correo** del administrador:

``ServerAdmin webmaster@localhost``

**Directorio** Raíz del Sitio Virtual:

``DocumentRoot /var/www/html``

**Directivas** **Características** y **rectriciones** del sitio Virtual Ejemplo:

![ConfigiracionBasica](../../../imagenes/apache2/directoryBasica.jpg)


| Directivas Options: |
| -- |
Algunas de las opciones que podemos indicar son las siguientes:
    • All: Todas las opciones excepto MultiViews.
    • FollowSymLinks: Se pueden seguir los enlaces simbólicos. Si esta opción está activada, podemos a través de enlaces simbólicos, archivos que estén fuera del directorio Document Root.

    • Indexes: Cuando accedemos al directorio y no se encuentra un fichero por defecto (indicado en la directiva DirectoryIndex del módulo mod_dir), por ejemplo el index.html, se muestra la lista de ficheros (esto lo realiza el módulo mod_autoindex).

    • MultiViews: Permite la negociación de contenido, mediante el módulo mod_negotiation. Por ejemplo: Ofrecer una página en un determinado idioma.

    • SymLinksIfOwnerMatch: Se pueden seguir enlaces simbólicos, sólo cuando el fichero destino es del mismo propietario que el enlace simbólico.

    • ExecCGI: Permite ejecutar script CGI (interfaz) usando el módulo mod_cgi.

Podemos activar o desactivar una opción en referencia con la configuración de un directorio padre mediante el signo + o -.
_________________________________________________
*[Volver atrás...](../README.md)*

*[Volver a página de inicio...](../../../README.md)*