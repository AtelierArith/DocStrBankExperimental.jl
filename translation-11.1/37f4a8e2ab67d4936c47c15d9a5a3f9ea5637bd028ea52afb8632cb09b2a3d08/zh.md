```
launch(manager::ClusterManager, params::Dict, launched::Array, launch_ntfy::Condition)
```

由集群管理器实现。对于通过此函数启动的每个Julia工作者，它应将一个`WorkerConfig`条目附加到`launched`中，并通知`launch_ntfy`。一旦所有由`manager`请求的工作者都已启动，该函数必须退出。`params`是调用时所有关键字参数的字典[`addprocs`](@ref)。
