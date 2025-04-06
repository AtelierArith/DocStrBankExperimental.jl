```
redirect_stdio(;stdin=stdin, stderr=stderr, stdout=stdout)
```

重定向一部分流 `stdin`、`stderr`、`stdout`。每个参数必须是 `IOStream`、`TTY`、[`Pipe`](@ref)、套接字或 `devnull`。

!!! compat "Julia 1.7"
    `redirect_stdio` 需要 Julia 1.7 或更高版本。

