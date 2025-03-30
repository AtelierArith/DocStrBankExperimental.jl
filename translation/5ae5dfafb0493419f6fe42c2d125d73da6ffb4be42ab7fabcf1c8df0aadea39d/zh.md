```
default_worker_pool()
```

[`AbstractWorkerPool`](@ref) 包含空闲的 [`workers`](@ref) - 被 `remote(f)` 和 [`pmap`](@ref)（默认情况下）使用。除非通过 `default_worker_pool!(pool)` 显式设置，否则默认工作池初始化为 [`WorkerPool`](@ref)。

# 示例

```julia-repl
$ julia -p 3

julia> default_worker_pool()
WorkerPool(Channel{Int64}(sz_max:9223372036854775807,sz_curr:3), Set([4, 2, 3]), RemoteChannel{Channel{Any}}(1, 1, 4))
```
