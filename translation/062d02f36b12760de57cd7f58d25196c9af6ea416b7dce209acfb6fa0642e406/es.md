```
kill(manager::ClusterManager, pid::Int, config::WorkerConfig)
```

Implementado por los administradores de clúster. Se llama en el proceso maestro, por [`rmprocs`](@ref). Debería hacer que el trabajador remoto especificado por `pid` salga. `kill(manager::ClusterManager.....)` ejecuta un `exit()` remoto en `pid`.
