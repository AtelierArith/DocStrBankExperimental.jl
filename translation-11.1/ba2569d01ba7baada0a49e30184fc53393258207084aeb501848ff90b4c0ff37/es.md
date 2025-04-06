```
ca_roots() :: Union{Nothing, String}
```

La función `ca_roots()` indica al llamador dónde, si es que hay algún lugar, encontrar un archivo o directorio de raíces de autoridad de certificación codificadas en PEM. Por defecto, en sistemas como Windows y macOS donde los motores TLS integrados saben cómo verificar hosts utilizando el mecanismo de verificación de certificados integrado del sistema, esta función devolverá `nothing`. En sistemas UNIX clásicos (excluyendo macOS), los certificados raíz se almacenan típicamente en un archivo en `/etc`: se buscarán los lugares comunes para el sistema UNIX actual y si uno de estos caminos existe, se devolverá; si ninguno de estos caminos típicos de certificados raíz existe, entonces se devolverá la ruta al conjunto de certificados raíz que están empaquetados con Julia.

El valor predeterminado devuelto por `ca_roots()` puede ser anulado configurando las variables de entorno `JULIA_SSL_CA_ROOTS_PATH`, `SSL_CERT_DIR` o `SSL_CERT_FILE`, en cuyo caso esta función siempre devolverá el valor de la primera de estas variables que esté configurada (ya sea que la ruta exista o no). Si `JULIA_SSL_CA_ROOTS_PATH` se establece en la cadena vacía, entonces se ignoran las otras variables (como si no estuvieran configuradas); si las otras variables se establecen en la cadena vacía, se comportan como si no estuvieran configuradas.
