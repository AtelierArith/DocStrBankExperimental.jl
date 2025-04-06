```
redirect_stdin([stream]) -> stream
```

[`stdout`](@ref) için [`redirect_stdout`](@ref) gibi, ancak [`stdin`](@ref) için. Akışın yönünün tersine döndüğünü unutmayın.

!!! note
    `stream` uyumlu bir nesne olmalıdır, örneğin bir `IOStream`, `TTY`, [`Pipe`](@ref), soket veya `devnull`.


Ayrıca bkz. [`redirect_stdio`](@ref).
