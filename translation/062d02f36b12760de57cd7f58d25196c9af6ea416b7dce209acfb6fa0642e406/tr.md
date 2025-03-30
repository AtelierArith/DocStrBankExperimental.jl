```
kill(manager::ClusterManager, pid::Int, config::WorkerConfig)
```

Küme yöneticileri tarafından uygulanır. Ana süreçte, [`rmprocs`](@ref) tarafından çağrılır. `pid` ile belirtilen uzak işçinin çıkmasını sağlamalıdır. `kill(manager::ClusterManager.....)` `pid` üzerinde uzak bir `exit()` çalıştırır.
