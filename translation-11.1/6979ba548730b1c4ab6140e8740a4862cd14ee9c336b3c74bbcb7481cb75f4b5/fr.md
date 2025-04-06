```
getaddrinfo(host::AbstractString) -> IPAddr
```

Obtient la première adresse IP disponible de `host`, qui peut être soit une adresse `IPv4` soit une adresse `IPv6`. Utilise l'implémentation getaddrinfo sous-jacente du système d'exploitation, qui peut effectuer une recherche DNS.
