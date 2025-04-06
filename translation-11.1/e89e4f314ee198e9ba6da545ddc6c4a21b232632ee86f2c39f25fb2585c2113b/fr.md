```
listen([addr, ]port::Integer; backlog::Integer=BACKLOG_DEFAULT) -> TCPServer
```

Écoute sur le port à l'adresse spécifiée par `addr`. Par défaut, cela écoute uniquement sur `localhost`. Pour écouter sur toutes les interfaces, passez `IPv4(0)` ou `IPv6(0)` selon le cas. `backlog` détermine combien de connexions peuvent être en attente (n'ayant pas appelé [`accept`](@ref)) avant que le serveur ne commence à les rejeter. La valeur par défaut de `backlog` est 511.
