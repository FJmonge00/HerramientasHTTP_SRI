#  Autenticación compleja

## Políticas de acceso en Apache 2.2

El control de acceso en versiones anteriores de Apache2, se hacía con las directivas Order, Allow y Deny. Además teníamos otra directiva Satisfy (Nota: Esta directiva no existe en Apache 2.4) que nos permitía controlar como el se debía comportar el servidor cuando tenemos varios instrucciones de control de acceso (allow, deny , require). de esta manera:

- Satisfy All: Se tenían que cumplir todas las condiciones para obtener el acceso.
- Satisfy Any: Bastaba con que se cumpliera una de las condiciones.

*Ejemplo:*

```apache
<Directory /dashboard>
    Order deny,allow
    Deny from all
    Allow from 10.1 → Pueden acceder todos los que procedan de la red 10.1
    Require group admins → Pueden acceder los que vengan del grupo admins
    Satisfy any → Se debe cumplir una de las condiciones anteriores para acceder.
</Directory>    
```