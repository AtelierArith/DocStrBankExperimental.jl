```
kill(manager::ClusterManager, pid::Int, config::WorkerConfig)
```

Implémenté par les gestionnaires de cluster. Il est appelé sur le processus maître, par [`rmprocs`](@ref). Cela devrait amener le travailleur distant spécifié par `pid` à quitter. `kill(manager::ClusterManager.....)` exécute un `exit()` distant sur `pid`.
