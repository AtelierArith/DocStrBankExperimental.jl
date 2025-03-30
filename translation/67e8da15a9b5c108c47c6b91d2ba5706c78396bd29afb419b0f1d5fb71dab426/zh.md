```
myid()
```

获取当前进程的 ID。

# 示例

```julia-repl
julia> myid()
1

julia> remotecall_fetch(() -> myid(), 4)
4
```
