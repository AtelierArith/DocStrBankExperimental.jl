```
redirect_stdout([stream]) -> stream
```

创建一个管道，所有 C 和 Julia 级别的 [`stdout`](@ref) 输出将被重定向到该管道。返回一个表示管道两端的流。写入 [`stdout`](@ref) 的数据现在可以从管道的 `rd` 端读取。

!!! note
    `stream` 必须是兼容的对象，例如 `IOStream`、`TTY`、[`Pipe`](@ref)、套接字或 `devnull`。


另见 [`redirect_stdio`](@ref)。
