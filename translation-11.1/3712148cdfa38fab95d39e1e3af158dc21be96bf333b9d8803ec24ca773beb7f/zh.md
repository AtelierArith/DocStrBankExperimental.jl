```
procs()
```

返回所有进程标识符的列表，包括 pid 1（该进程不包括在 [`workers()`](@ref) 中）。

# 示例

```julia-repl
$ julia -p 2

julia> procs()
3-element Array{Int64,1}:
 1
 2
 3
```
