```
ca_roots_path() :: String
```

La función `ca_roots_path()` es similar a la función `ca_roots()`, excepto que siempre devuelve una ruta a un archivo o directorio de raíces de autoridad de certificación codificadas en PEM. Cuando se llama en un sistema como Windows o macOS, donde los certificados raíz del sistema no se almacenan en el sistema de archivos, actualmente devolverá la ruta al conjunto de certificados raíz que están empaquetados con Julia. (En el futuro, esta función podría extraer los certificados raíz del sistema y guardarlos en un archivo cuya ruta se devolvería).

Si es posible configurar una biblioteca que use TLS para utilizar los certificados del sistema, eso es generalmente preferible: es decir, es mejor usar `ca_roots()` que devuelve `nothing` para indicar que se deben usar los certificados del sistema. La función `ca_roots_path()` solo debe usarse al configurar bibliotecas que *requieren* una ruta a un archivo o directorio para los certificados raíz.

El valor predeterminado devuelto por `ca_roots_path()` puede ser anulado configurando las variables de entorno `JULIA_SSL_CA_ROOTS_PATH`, `SSL_CERT_DIR` o `SSL_CERT_FILE`, en cuyo caso esta función siempre devolverá el valor de la primera de estas variables que esté configurada (ya sea que la ruta exista o no). Si `JULIA_SSL_CA_ROOTS_PATH` se establece en la cadena vacía, entonces se ignoran las otras variables (como si no estuvieran configuradas); si las otras variables se establecen en la cadena vacía, se comportan como si no estuvieran configuradas.
