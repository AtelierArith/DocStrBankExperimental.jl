```
redirect_stdout([stream]) -> stream
```

Crea un pipe al que se redirigirá toda la salida de nivel C y Julia [`stdout`](@ref). Devuelve un flujo que representa los extremos del pipe. Los datos escritos en [`stdout`](@ref) ahora se pueden leer desde el extremo `rd` del pipe.

!!! nota
    `stream` debe ser un objeto compatible, como un `IOStream`, `TTY`, [`Pipe`](@ref), socket o `devnull`.


Consulta también [`redirect_stdio`](@ref).
