```
init_worker(cookie::AbstractString, manager::ClusterManager=DefaultClusterManager())
```

Aufgerufen von Cluster-Managern, die benutzerdefinierte Transports implementieren. Es initialisiert einen neu gestarteten Prozess als Arbeiter. Das Befehlszeilenargument `--worker[=<cookie>]` hat die Wirkung, einen Prozess als Arbeiter zu initialisieren, der TCP/IP-Sockets für den Transport verwendet. `cookie` ist ein [`cluster_cookie`](@ref).
