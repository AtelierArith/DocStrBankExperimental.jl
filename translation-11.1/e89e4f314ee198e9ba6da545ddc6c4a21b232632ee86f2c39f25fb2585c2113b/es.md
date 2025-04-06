```
listen([addr, ]port::Integer; backlog::Integer=BACKLOG_DEFAULT) -> TCPServer
```

Escucha en el puerto en la dirección especificada por `addr`. Por defecto, esto escucha solo en `localhost`. Para escuchar en todas las interfaces, pasa `IPv4(0)` o `IPv6(0)` según corresponda. `backlog` determina cuántas conexiones pueden estar pendientes (sin haber llamado a [`accept`](@ref)) antes de que el servidor comience a rechazarlas. El valor predeterminado de `backlog` es 511.
