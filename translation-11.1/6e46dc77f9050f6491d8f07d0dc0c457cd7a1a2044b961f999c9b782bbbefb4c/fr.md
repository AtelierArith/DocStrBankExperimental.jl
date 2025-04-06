```
init_worker(cookie::AbstractString, manager::ClusterManager=DefaultClusterManager())
```

Appelé par les gestionnaires de cluster implémentant des transports personnalisés. Il initialise un processus nouvellement lancé en tant que travailleur. L'argument de ligne de commande `--worker[=<cookie>]` a pour effet d'initialiser un processus en tant que travailleur utilisant des sockets TCP/IP pour le transport. `cookie` est un [`cluster_cookie`](@ref).
