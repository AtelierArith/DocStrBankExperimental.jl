```
@spawn expr
```

创建一个围绕表达式的闭包，并在自动选择的进程上运行它，返回一个 [`Future`](@ref) 结果。此宏已被弃用；应使用 `@spawnat :any expr`。

# 示例

```julia-repl
julia> addprocs(3);

julia> f = @spawn myid()
Future(2, 1, 5, nothing)

julia> fetch(f)
2

julia> f = @spawn myid()
Future(3, 1, 7, nothing)

julia> fetch(f)
3
```

!!! compat "Julia 1.3"
    从 Julia 1.3 开始，此宏已被弃用。请改用 `@spawnat :any`。

