```
redirect_stderr([stream]) -> stream
```

Comme [`redirect_stdout`](@ref), mais pour [`stderr`](@ref).

!!! note
    `stream` doit être un objet compatible, tel qu'un `IOStream`, `TTY`, [`Pipe`](@ref), socket, ou `devnull`.


Voir aussi [`redirect_stdio`](@ref).
