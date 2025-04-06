```
undef
```

Alias para `UndefInitializer()`, que construye una instancia del tipo singleton [`UndefInitializer`](@ref), utilizado en la inicialización de arreglos para indicar que el llamador del constructor de arreglos desea un arreglo no inicializado.

Ver también: [`missing`](@ref), [`similar`](@ref).

# Ejemplos

```julia-repl
julia> Array{Float64, 1}(undef, 3)
3-element Vector{Float64}:
 2.2752528595e-314
 2.202942107e-314
 2.275252907e-314
```
