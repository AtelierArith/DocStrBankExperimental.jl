```
bind(socket::Union{TCPServer, UDPSocket, TCPSocket}, host::IPAddr, port::Integer; ipv6only=false, reuseaddr=false, kws...)
```

Binde `socket` an den angegebenen `host:port`. Beachten Sie, dass `0.0.0.0` auf allen Geräten lauscht.

  * Der Parameter `ipv6only` deaktiviert den Dual-Stack-Modus. Wenn `ipv6only=true`, wird nur ein IPv6-Stack erstellt.
  * Wenn `reuseaddr=true`, können mehrere Threads oder Prozesse an dieselbe Adresse binden, ohne einen Fehler zu verursachen, wenn sie alle `reuseaddr=true` setzen, aber nur der letzte, der bindet, erhält den gesamten Verkehr.
