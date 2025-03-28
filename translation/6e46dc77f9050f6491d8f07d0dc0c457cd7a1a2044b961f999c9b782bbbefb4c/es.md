```
init_worker(cookie::AbstractString, manager::ClusterManager=DefaultClusterManager())
```

Llamado por administradores de clúster que implementan transportes personalizados. Inicializa un proceso recién lanzado como un trabajador. El argumento de línea de comandos `--worker[=<cookie>]` tiene el efecto de inicializar un proceso como un trabajador utilizando sockets TCP/IP para el transporte. `cookie` es un [`cluster_cookie`](@ref).
