```
undef
```

Alias für `UndefInitializer()`, das eine Instanz des Singleton-Typs [`UndefInitializer`](@ref) erstellt, der bei der Array-Initialisierung verwendet wird, um anzuzeigen, dass der Array-Konstruktor-Aufrufer ein uninitialisiertes Array wünscht.

Siehe auch: [`missing`](@ref), [`similar`](@ref).

# Beispiele

```julia-repl
julia> Array{Float64, 1}(undef, 3)
3-element Vector{Float64}:
 2.2752528595e-314
 2.202942107e-314
 2.275252907e-314
```
