```
getalladdrinfo(host::AbstractString) -> Vector{IPAddr}
```

Obtient toutes les adresses IP du `host`. Utilise l'implémentation sous-jacente de `getaddrinfo` du système d'exploitation, qui peut effectuer une recherche DNS.

# Exemples

```julia-repl
julia> getalladdrinfo("google.com")
2-element Array{IPAddr,1}:
 ip"172.217.6.174"
 ip"2607:f8b0:4000:804::200e"
```
