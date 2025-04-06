```
redirect_stdin([stream]) -> stream
```

类似于 [`redirect_stdout`](@ref)，但用于 [`stdin`](@ref)。请注意，流的方向是相反的。

!!! note
    `stream` 必须是兼容的对象，例如 `IOStream`、`TTY`、[`Pipe`](@ref)、套接字或 `devnull`。


另见 [`redirect_stdio`](@ref)。
