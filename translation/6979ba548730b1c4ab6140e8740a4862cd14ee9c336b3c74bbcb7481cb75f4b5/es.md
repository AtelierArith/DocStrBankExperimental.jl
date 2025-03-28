```
getaddrinfo(host::AbstractString) -> IPAddr
```

Obtiene la primera dirección IP disponible de `host`, que puede ser una dirección `IPv4` o `IPv6`. Utiliza la implementación subyacente de getaddrinfo del sistema operativo, que puede realizar una búsqueda DNS.
