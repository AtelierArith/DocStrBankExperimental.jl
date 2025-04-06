```
@spawnat p expr
```

创建一个围绕表达式的闭包，并在进程 `p` 上异步运行该闭包。返回一个 [`Future`](@ref) 结果。如果 `p` 是引用的字面符号 `:any`，则系统将自动选择一个处理器来使用。

# 示例

```julia-repl
julia> addprocs(3);

julia> f = @spawnat 2 myid()
Future(2, 1, 3, nothing)

julia> fetch(f)
2

julia> f = @spawnat :any myid()
Future(3, 1, 7, nothing)

julia> fetch(f)
3
```

!!! compat "Julia 1.3"
    `:any` 参数自 Julia 1.3 起可用。

