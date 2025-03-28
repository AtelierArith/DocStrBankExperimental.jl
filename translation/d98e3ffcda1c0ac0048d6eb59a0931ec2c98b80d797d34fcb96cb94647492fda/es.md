```
recvfrom(socket::UDPSocket) -> (host_port, data)
```

Lee un paquete UDP del socket especificado, devolviendo una tupla de `(host_port, data)`, donde `host_port` será un InetAddr{IPv4} o InetAddr{IPv6}, según corresponda.

!!! compat "Julia 1.3"
    Antes de la versión 1.3 de Julia, el primer valor devuelto era una dirección (`IPAddr`). En la versión 1.3 se cambió a un `InetAddr`.

