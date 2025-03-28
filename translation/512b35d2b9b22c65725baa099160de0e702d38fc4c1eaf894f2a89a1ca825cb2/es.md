```
getaddrinfo(host::AbstractString, IPAddr) -> IPAddr
```

Obtiene la primera dirección IP del `host` del tipo `IPAddr` especificado. Utiliza la implementación subyacente de getaddrinfo del sistema operativo, que puede realizar una búsqueda DNS.

# Ejemplos

```julia-repl
julia> getaddrinfo("localhost", IPv6)
ip"::1"

julia> getaddrinfo("localhost", IPv4)
ip"127.0.0.1"
```
