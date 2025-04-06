```
redirect_stdio(f; stdin=nothing, stderr=nothing, stdout=nothing)
```

重定向部分流 `stdin`、`stderr`、`stdout`，调用 `f()` 并恢复每个流。

每个流的可能值为：

  * `nothing` 表示该流不应被重定向。
  * `path::AbstractString` 将流重定向到 `path` 处的文件。
  * `io` 一个 `IOStream`、`TTY`、[`Pipe`](@ref)、套接字或 `devnull`。

# 示例

```julia-repl
julia> redirect_stdio(stdout="stdout.txt", stderr="stderr.txt") do
           print("hello stdout")
           print(stderr, "hello stderr")
       end

julia> read("stdout.txt", String)
"hello stdout"

julia> read("stderr.txt", String)
"hello stderr"
```

# 边缘情况

可以将相同的参数传递给 `stdout` 和 `stderr`：

```julia-repl
julia> redirect_stdio(stdout="log.txt", stderr="log.txt", stdin=devnull) do
    ...
end
```

但是不支持传递同一文件的两个不同描述符。

```julia-repl
julia> io1 = open("same/path", "w")

julia> io2 = open("same/path", "w")

julia> redirect_stdio(f, stdout=io1, stderr=io2) # 不支持
```

此外，`stdin` 参数不能与 `stdout` 或 `stderr` 是相同的描述符。

```julia-repl
julia> io = open(...)

julia> redirect_stdio(f, stdout=io, stdin=io) # 不支持
```

!!! compat "Julia 1.7"
    `redirect_stdio` 需要 Julia 1.7 或更高版本。

