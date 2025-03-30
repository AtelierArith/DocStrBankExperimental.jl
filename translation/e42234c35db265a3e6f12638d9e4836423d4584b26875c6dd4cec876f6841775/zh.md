```
manage(manager::ClusterManager, id::Integer, config::WorkerConfig. op::Symbol)
```

由集群管理器实现。它在主进程中被调用，在工作者的生命周期内，使用适当的 `op` 值：

  * 当工作者被添加/移除到/从 Julia 工作者池时，使用 `:register`/`:deregister`。
  * 当调用 `interrupt(workers)` 时，使用 `:interrupt`。`ClusterManager` 应该向适当的工作者发送中断信号。
  * 使用 `:finalize` 进行清理。
