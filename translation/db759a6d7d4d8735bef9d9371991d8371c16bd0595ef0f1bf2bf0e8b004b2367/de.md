```
hardlink(src::AbstractString, dst::AbstractString)
```

Erstellt einen Hardlink zu einer vorhandenen Quelldatei `src` mit dem Namen `dst`. Das Ziel, `dst`, darf nicht existieren.

Siehe auch: [`symlink`](@ref).

!!! compat "Julia 1.8"
    Diese Methode wurde in Julia 1.8 hinzugefügt.

