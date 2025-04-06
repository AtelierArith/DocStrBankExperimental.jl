```
remotecall_fetch(f, id::Integer, args...; kwargs...)
```

在一条消息中执行 `fetch(remotecall(...))`。关键字参数（如果有）将传递给 `f`。任何远程异常都将被捕获在 [`RemoteException`](@ref) 中并抛出。

另请参见 [`fetch`](@ref) 和 [`remotecall`](@ref)。

# 示例

```julia-repl
$ julia -p 2

julia> remotecall_fetch(sqrt, 2, 4)
2.0

julia> remotecall_fetch(sqrt, 2, -4)
ERROR: 在工作节点 2:
DomainError with -4.0:
sqrt 被调用时使用了负实数参数，但仅在使用复数参数时才会返回复数结果。尝试 sqrt(Complex(x))。
...
```
