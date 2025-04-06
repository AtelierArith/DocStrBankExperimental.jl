```
isready(rr::Future)
```

确定一个 [`Future`](@ref) 是否有值存储。

如果参数 `Future` 被不同的节点拥有，此调用将会阻塞以等待答案。建议在单独的任务中等待 `rr`，或者使用本地的 [`Channel`](@ref) 作为代理：

```julia
p = 1
f = Future(p)
errormonitor(@async put!(f, remotecall_fetch(long_computation, p)))
isready(f)  # 不会阻塞
```
