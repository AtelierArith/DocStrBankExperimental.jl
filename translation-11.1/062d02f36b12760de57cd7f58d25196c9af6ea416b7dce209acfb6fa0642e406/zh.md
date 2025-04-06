```
kill(manager::ClusterManager, pid::Int, config::WorkerConfig)
```

由集群管理器实现。它在主进程中被 [`rmprocs`](@ref) 调用。它应该导致由 `pid` 指定的远程工作者退出。`kill(manager::ClusterManager.....)` 在 `pid` 上执行远程 `exit()`。
