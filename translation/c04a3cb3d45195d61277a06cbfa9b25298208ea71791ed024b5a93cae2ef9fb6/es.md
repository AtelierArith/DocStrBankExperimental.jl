```
redirect_stdin([stream]) -> stream
```

Como [`redirect_stdout`](@ref), pero para [`stdin`](@ref). Tenga en cuenta que la dirección del flujo está invertida.

!!! nota
    `stream` debe ser un objeto compatible, como un `IOStream`, `TTY`, [`Pipe`](@ref), socket o `devnull`.


Véase también [`redirect_stdio`](@ref).
