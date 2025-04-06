```
redirect_stdio(;stdin=stdin, stderr=stderr, stdout=stdout)
```

Redirige un sous-ensemble des flux `stdin`, `stderr`, `stdout`. Chaque argument doit être un `IOStream`, `TTY`, [`Pipe`](@ref), socket ou `devnull`.

!!! compat "Julia 1.7"
    `redirect_stdio` nécessite Julia 1.7 ou une version ultérieure.

