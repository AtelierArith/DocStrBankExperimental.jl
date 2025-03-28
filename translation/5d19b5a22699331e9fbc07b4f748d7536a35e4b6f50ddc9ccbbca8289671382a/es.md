```
verify_host(url::AbstractString, [transport::AbstractString]) :: Bool
```

La función `verify_host` indica al llamador si se debe verificar la identidad de un host al comunicarse a través de transportes seguros como TLS o SSH. El argumento `url` puede ser:

1. una URL adecuada que comience con `proto://`
2. un nombre de host desnudo al estilo `ssh` o un nombre de host precedido por `user@`
3. un host al estilo `scp` como se mencionó anteriormente, seguido de `:` y una ubicación de ruta

En cada caso, la parte del nombre del host se extrae y la decisión sobre si verificar o no se toma únicamente en función del nombre del host, no de nada más sobre la URL de entrada. En particular, el protocolo de la URL no importa (más abajo).

El argumento `transport` indica el tipo de transporte sobre el que se realiza la consulta. Los valores actualmente conocidos son `SSL`/`ssl` (alias `TLS`/`tls`) y `SSH`/`ssh`. Si se omite el transporte, la consulta devolverá `true` solo si el nombre del host no debe ser verificado independientemente del transporte.

El nombre del host se compara con los patrones de host en las variables de entorno relevantes dependiendo de si se proporciona `transport` y cuál es su valor:

  * `JULIA_NO_VERIFY_HOSTS` — hosts que no deben ser verificados para ningún transporte
  * `JULIA_SSL_NO_VERIFY_HOSTS` — hosts que no deben ser verificados para SSL/TLS
  * `JULIA_SSH_NO_VERIFY_HOSTS` — hosts que no deben ser verificados para SSH
  * `JULIA_ALWAYS_VERIFY_HOSTS` — hosts que siempre deben ser verificados

Los valores de cada una de estas variables son una lista separada por comas de patrones de nombres de host con la siguiente sintaxis: cada patrón se divide en `.` en partes y cada parte debe ser una de:

1. Un componente de nombre de dominio literal que consiste en una o más letras ASCII, dígitos, guiones o guiones bajos (técnicamente no es parte de un nombre de host legal, pero a veces se usa). Un componente de nombre de dominio literal coincide solo consigo mismo.
2. Un `**`, que coincide con cero o más componentes de nombre de dominio.
3. Un `*`, que coincide con cualquier componente de nombre de dominio.

Al comparar un nombre de host con una lista de patrones en una de estas variables, el nombre del host se divide en `.` en componentes y esa secuencia de palabras se compara con el patrón: un patrón literal coincide exactamente con un componente de nombre de host con ese valor; un patrón `*` coincide exactamente con un componente de nombre de host con cualquier valor; un patrón `**` coincide con cualquier número de componentes de nombre de host. Por ejemplo:

  * `**` coincide con cualquier nombre de host
  * `**.org` coincide con cualquier nombre de host en el dominio de nivel superior `.org`
  * `example.com` coincide solo con el nombre de host exacto `example.com`
  * `*.example.com` coincide con `api.example.com` pero no con `example.com` o `v1.api.example.com`
  * `**.example.com` coincide con cualquier dominio bajo `example.com`, incluyendo `example.com` mismo, `api.example.com` y `v1.api.example.com`

```
