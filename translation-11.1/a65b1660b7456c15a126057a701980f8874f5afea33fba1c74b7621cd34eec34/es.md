```
getnameinfo(host::IPAddr) -> String
```

Realiza una búsqueda inversa para la dirección IP para devolver un nombre de host y un servicio utilizando la implementación subyacente `getnameinfo` del sistema operativo.

# Ejemplos

```julia-repl
julia> getnameinfo(IPv4("8.8.8.8"))
"google-public-dns-a.google.com"
```
