```
setopt(sock::UDPSocket; multicast_loop=nothing, multicast_ttl=nothing, enable_broadcast=nothing, ttl=nothing)
```

Establecer opciones del socket UDP.

  * `multicast_loop`: bucle de retorno para paquetes multicast (predeterminado: `true`).
  * `multicast_ttl`: TTL para paquetes multicast (predeterminado: `nothing`).
  * `enable_broadcast`: la bandera debe establecerse en `true` si el socket se utilizará para mensajes de difusión, de lo contrario, el sistema UDP devolverá un error de acceso (predeterminado: `false`).
  * `ttl`: Tiempo de vida de los paquetes enviados por el socket (predeterminado: `nothing`).
