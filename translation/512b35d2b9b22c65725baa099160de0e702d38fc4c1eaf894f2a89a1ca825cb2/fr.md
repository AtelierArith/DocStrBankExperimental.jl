```
getaddrinfo(host::AbstractString, IPAddr) -> IPAddr
```

Obtient la première adresse IP de l'`hôte` du type `IPAddr` spécifié. Utilise l'implémentation getaddrinfo sous-jacente du système d'exploitation, qui peut effectuer une recherche DNS.

# Exemples

```julia-repl
julia> getaddrinfo("localhost", IPv6)
ip"::1"

julia> getaddrinfo("localhost", IPv4)
ip"127.0.0.1"
```
