```
redirect_stdio(;stdin=stdin, stderr=stderr, stdout=stdout)
```

`stdin`, `stderr`, `stdout` akışlarının bir alt kümesini yönlendirin. Her argüman bir `IOStream`, `TTY`, [`Pipe`](@ref), soket veya `devnull` olmalıdır.

!!! uyumluluk "Julia 1.7"
    `redirect_stdio` Julia 1.7 veya daha yenisini gerektirir.

