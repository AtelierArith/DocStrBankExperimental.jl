```
redirect_stderr([stream]) -> stream
```

Wie [`redirect_stdout`](@ref), aber für [`stderr`](@ref).

!!! Hinweis     `stream` muss ein kompatibles Objekt sein, wie ein `IOStream`, `TTY`, [`Pipe`](@ref), Socket oder `devnull`.

Siehe auch [`redirect_stdio`](@ref).
