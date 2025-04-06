```
hardlink(src::AbstractString, dst::AbstractString)
```

Crea un enlace duro a un archivo fuente existente `src` con el nombre `dst`. El destino, `dst`, no debe existir.

Ver también: [`symlink`](@ref).

!!! compat "Julia 1.8"
    Este método se agregó en Julia 1.8.

