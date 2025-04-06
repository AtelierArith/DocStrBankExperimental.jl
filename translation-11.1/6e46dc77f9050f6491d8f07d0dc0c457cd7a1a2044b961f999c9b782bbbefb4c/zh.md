```
init_worker(cookie::AbstractString, manager::ClusterManager=DefaultClusterManager())
```

由实现自定义传输的集群管理器调用。它将新启动的进程初始化为工作者。命令行参数 `--worker[=<cookie>]` 的效果是使用 TCP/IP 套接字将进程初始化为工作者。`cookie` 是一个 [`cluster_cookie`](@ref)。
