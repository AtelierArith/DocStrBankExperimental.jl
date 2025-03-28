```
mktempdir(f::Function, parent=tempdir(); prefix="jl_")
```

Aplica la función `f` al resultado de [`mktempdir(parent; prefix)`](@ref) y elimina el directorio temporal y todo su contenido al finalizar.

Véase también: [`mktemp`](@ref), [`mkdir`](@ref).

!!! compat "Julia 1.2"
    El argumento de palabra clave `prefix` se agregó en Julia 1.2.

