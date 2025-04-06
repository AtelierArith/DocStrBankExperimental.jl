```
ssh_known_hosts_files() :: Vector{String}
```

La función `ssh_known_hosts_files()` devuelve un vector de rutas de archivos de hosts conocidos de SSH que deben ser utilizados al establecer las identidades de los servidores remotos para conexiones SSH. Por defecto, esta función devuelve

```
[joinpath(ssh_dir(), "known_hosts"), bundled_known_hosts]
```

donde `bundled_known_hosts` es la ruta de una copia de un archivo de hosts conocidos que está empaquetado con este paquete (que contiene claves de hosts conocidos para `github.com` y `gitlab.com`). Sin embargo, si la variable de entorno `SSH_KNOWN_HOSTS_FILES` está configurada, su valor se divide en rutas en el carácter `:` (o en `;` en Windows) y este vector de rutas se devuelve en su lugar. Si algún componente de este vector está vacío, se expande a las rutas de hosts conocidos por defecto.

Los paquetes que utilizan `ssh_known_hosts_files()` deberían idealmente buscar entradas coincidentes comparando el nombre del host y los tipos de clave, considerando la primera entrada en cualquiera de los archivos que coincida como la identidad definitiva del host. Si el llamador no puede comparar el tipo de clave (por ejemplo, porque ha sido hasheada), entonces debe aproximar el algoritmo anterior buscando todas las entradas coincidentes para un host en cada archivo: si un archivo tiene alguna entrada para un host, entonces una de ellas debe coincidir; el llamador solo debe continuar buscando en otros archivos de hosts conocidos si no hay entradas para el host en cuestión en un archivo anterior.
