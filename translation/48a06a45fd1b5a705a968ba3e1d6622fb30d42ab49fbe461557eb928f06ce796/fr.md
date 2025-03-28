```
undef
```

Alias pour `UndefInitializer()`, qui construit une instance du type singleton [`UndefInitializer`](@ref), utilisé dans l'initialisation de tableau pour indiquer que l'appelant du constructeur de tableau souhaite un tableau non initialisé.

Voir aussi : [`missing`](@ref), [`similar`](@ref).

# Exemples

```julia-repl
julia> Array{Float64, 1}(undef, 3)
3-element Vector{Float64}:
 2.2752528595e-314
 2.202942107e-314
 2.275252907e-314
```
