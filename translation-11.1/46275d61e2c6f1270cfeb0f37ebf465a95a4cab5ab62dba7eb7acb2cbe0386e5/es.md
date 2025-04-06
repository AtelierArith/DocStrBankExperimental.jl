```
mktemp(f::Function, parent=tempdir())
```

Aplica la función `f` al resultado de [`mktemp(parent)`](@ref) y elimina el archivo temporal al finalizar.

Véase también: [`mktempdir`](@ref).
