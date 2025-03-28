```
redirect_stdio(;stdin=stdin, stderr=stderr, stdout=stdout)
```

Redirigir un subconjunto de los flujos `stdin`, `stderr`, `stdout`. Cada argumento debe ser un `IOStream`, `TTY`, [`Pipe`](@ref), socket o `devnull`.

!!! compat "Julia 1.7"
    `redirect_stdio` requiere Julia 1.7 o posterior.

