```
UndefInitializer
```

Tipo singleton utilizado en la inicialización de arreglos, indicando que el llamador del constructor de arreglos desea un arreglo no inicializado. Ver también [`undef`](@ref), un alias para `UndefInitializer()`.

# Ejemplos

```julia-repl
julia> Array{Float64, 1}(UndefInitializer(), 3)
3-element Array{Float64, 1}:
 2.2752528595e-314
 2.202942107e-314
 2.275252907e-314
```
