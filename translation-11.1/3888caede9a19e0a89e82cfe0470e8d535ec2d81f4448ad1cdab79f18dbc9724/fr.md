```
UndefInitializer
```

Type singleton utilisé dans l'initialisation de tableau, indiquant que l'appelant du constructeur de tableau souhaite un tableau non initialisé. Voir aussi [`undef`](@ref), un alias pour `UndefInitializer()`.

# Exemples

```julia-repl
julia> Array{Float64, 1}(UndefInitializer(), 3)
3-element Array{Float64, 1}:
 2.2752528595e-314
 2.202942107e-314
 2.275252907e-314
```
