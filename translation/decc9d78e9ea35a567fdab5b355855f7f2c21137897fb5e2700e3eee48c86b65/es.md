```
redirect_stderr([stream]) -> stream
```

Como [`redirect_stdout`](@ref), pero para [`stderr`](@ref).

!!! nota
    `stream` debe ser un objeto compatible, como un `IOStream`, `TTY`, [`Pipe`](@ref), socket o `devnull`.


Véase también [`redirect_stdio`](@ref).
