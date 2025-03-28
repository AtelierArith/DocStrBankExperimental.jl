```
recvfrom(socket::UDPSocket) -> (host_port, data)
```

Lese ein UDP-Paket vom angegebenen Socket und gebe ein Tupel von `(host_port, data)` zurück, wobei `host_port` eine InetAddr{IPv4} oder InetAddr{IPv6} sein wird, je nach Bedarf.

!!! compat "Julia 1.3"
    Vor Julia-Version 1.3 war der erste zurückgegebene Wert eine Adresse (`IPAddr`). In Version 1.3 wurde er in eine `InetAddr` geändert.

