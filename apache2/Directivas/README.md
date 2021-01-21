# Directivas

## Directivas de control de la conexión.

``/etc/apache/apache2.conf``

**Timeout:** define, en segundos, el tiempo que el servidor esperará por recibir y transmitir durante la comunicación. Timeout está configurado por defecto a 300 segundos, lo cual es apropiado para la mayoría de las situaciones.
**Ejemplo:** A veces el servidor recibe o envía ficheros.

**KeepAlive:** Define si las conexiones persistentes están activadas. Por defecto están activadas.
Esto permite tener una única conexión TCP abierta y realizar varias peticiones.

**MaxKeepAliveRequests:** Establece el número máximo de peticiones permitidas por cada conexión persistente. Por defecto está establecido como 100.
Hasta 100 peticiones se puede realizar con la misma conexión TCP.

**KeepAliveTimeout:** Establece el número de segundos que el servidor esperará tras haber dado servicio a una petición, antes de cerrar la conexión. Por defecto 5 segundos.
El servidor espera 5 segundos a que el cliente le haga una petición. Si no realiza ninguna, se cierra la conexión TCP.

## Otras directivas.
**User:** define el usuario que ejecuta los procesos de Apache2. ``www-data``
**Group:** define el grupo al que corresponde el usuario. ``www-data``
![imagenusuariosygrupos](/imagenes/apache2/usuarioygrupoDirectivas.png)

**LogLevel:** Controla el nivel de información que se guarda en los ficheros de registro o logs.
**LogFormat:** Controla el formato de información que se va a guardar en los ficheros logs.
**Directory o DirectoryMatch:** Declara un contexto para un directorio y todos sus directorios. Son las opciones que le damos a los directorios.
**Files o FilesMatch:** Declara un contexto para un conjunto de ficheros. Son las opciones que le vamos a dar a los ficheros.

*Teoría obtenida de:* [mftienda](https://github.com/mftienda)