```
addprocs(manager::ClusterManager; kwargs...) -> 进程标识符列表
```

通过指定的集群管理器启动工作进程。

例如，通过在包 `ClusterManagers.jl` 中实现的自定义集群管理器支持 Beowulf 集群。

新启动的工作进程等待从主节点建立连接的秒数可以通过工作进程环境中的变量 `JULIA_WORKER_TIMEOUT` 指定。仅在使用 TCP/IP 作为传输时相关。

要在不阻塞 REPL 或者如果以编程方式启动工作进程的包含函数的情况下启动工作进程，请在其自己的任务中执行 `addprocs`。

# 示例

```julia
# 在繁忙的集群上，异步调用 `addprocs`
t = @async addprocs(...)
```

```julia
# 利用工作进程在它们上线时
if nprocs() > 1   # 确保至少有一个新工作进程可用
   ....   # 执行分布式计算
end
```

```julia
# 检索新启动的工作进程 ID 或任何错误消息
if istaskdone(t)   # 检查 `addprocs` 是否已完成，以确保 `fetch` 不会阻塞
    if nworkers() == N
        new_pids = fetch(t)
    else
        fetch(t)
    end
end
```
