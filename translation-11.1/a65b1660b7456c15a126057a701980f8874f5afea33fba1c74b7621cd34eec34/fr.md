```
getnameinfo(hôte::IPAddr) -> String
```

Effectue une recherche inversée pour l'adresse IP afin de retourner un nom d'hôte et un service en utilisant l'implémentation sous-jacente `getnameinfo` du système d'exploitation.

# Exemples

```julia-repl
julia> getnameinfo(IPv4("8.8.8.8"))
"google-public-dns-a.google.com"
```
