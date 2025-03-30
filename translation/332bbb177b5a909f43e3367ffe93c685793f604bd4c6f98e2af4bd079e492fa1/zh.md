```
nworkers()
```

获取可用工作进程的数量。这比 [`nprocs()`](@ref) 少一个。如果 `nprocs() == 1`，则等于 `nprocs()`。

# 示例

```julia-repl
$ julia -p 2

julia> nprocs()
3

julia> nworkers()
2
```
