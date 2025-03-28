```
redirect_stdin([stream]) -> stream
```

Wie [`redirect_stdout`](@ref), aber für [`stdin`](@ref). Beachten Sie, dass die Richtung des Streams umgekehrt ist.

!!! Hinweis     `stream` muss ein kompatibles Objekt sein, wie z.B. ein `IOStream`, `TTY`, [`Pipe`](@ref), Socket oder `devnull`.

Siehe auch [`redirect_stdio`](@ref).
