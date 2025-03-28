```
setopt(sock::UDPSocket; multicast_loop=nothing, multicast_ttl=nothing, enable_broadcast=nothing, ttl=nothing)
```

Setzen Sie die UDP-Socket-Optionen.

  * `multicast_loop`: Loopback für Multicast-Pakete (Standard: `true`).
  * `multicast_ttl`: TTL für Multicast-Pakete (Standard: `nothing`).
  * `enable_broadcast`: Flag muss auf `true` gesetzt werden, wenn der Socket für Broadcast-Nachrichten verwendet wird, andernfalls gibt das UDP-System einen Zugriffsfehler zurück (Standard: `false`).
  * `ttl`: Time-to-live von Paketen, die über den Socket gesendet werden (Standard: `nothing`).
