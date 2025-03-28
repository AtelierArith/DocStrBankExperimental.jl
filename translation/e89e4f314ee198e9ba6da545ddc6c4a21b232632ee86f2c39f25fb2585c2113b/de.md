```
listen([addr, ]port::Integer; backlog::Integer=BACKLOG_DEFAULT) -> TCPServer
```

Hören Sie auf dem Port an der durch `addr` angegebenen Adresse. Standardmäßig hört dies nur auf `localhost`. Um auf allen Schnittstellen zu hören, übergeben Sie `IPv4(0)` oder `IPv6(0)` je nach Bedarf. `backlog` bestimmt, wie viele Verbindungen ausstehend sein können (die [`accept`](@ref) nicht aufgerufen haben), bevor der Server beginnt, sie abzulehnen. Der Standardwert von `backlog` beträgt 511.
