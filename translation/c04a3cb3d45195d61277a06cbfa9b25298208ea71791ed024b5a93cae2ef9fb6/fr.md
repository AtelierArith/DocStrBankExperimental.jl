```
redirect_stdin([stream]) -> stream
```

Comme [`redirect_stdout`](@ref), mais pour [`stdin`](@ref). Notez que la direction du flux est inversée.

!!! note
    `stream` doit être un objet compatible, tel qu'un `IOStream`, `TTY`, [`Pipe`](@ref), socket ou `devnull`.


Voir aussi [`redirect_stdio`](@ref).
