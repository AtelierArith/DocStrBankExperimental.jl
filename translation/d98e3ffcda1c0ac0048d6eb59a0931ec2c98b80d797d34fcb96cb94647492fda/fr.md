```
recvfrom(socket::UDPSocket) -> (host_port, data)
```

Lire un paquet UDP à partir du socket spécifié, retournant un tuple de `(host_port, data)`, où `host_port` sera un InetAddr{IPv4} ou InetAddr{IPv6}, selon le cas.

!!! compat "Julia 1.3"
    Avant la version 1.3 de Julia, la première valeur retournée était une adresse (`IPAddr`). Dans la version 1.3, elle a été changée en `InetAddr`.

