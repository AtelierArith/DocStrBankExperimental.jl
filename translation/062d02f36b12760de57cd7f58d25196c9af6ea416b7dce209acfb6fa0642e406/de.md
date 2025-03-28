```
kill(manager::ClusterManager, pid::Int, config::WorkerConfig)
```

Wird von Cluster-Managern implementiert. Es wird im Master-Prozess von [`rmprocs`](@ref) aufgerufen. Es sollte dazu führen, dass der entfernte Worker, der durch `pid` angegeben ist, beendet wird. `kill(manager::ClusterManager.....)` führt ein entferntes `exit()` auf `pid` aus.
