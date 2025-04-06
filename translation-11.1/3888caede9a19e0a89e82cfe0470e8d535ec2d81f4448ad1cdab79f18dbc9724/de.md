```
UndefInitializer
```

Singleton-Typ, der bei der Array-Initialisierung verwendet wird und anzeigt, dass der Array-Konstruktor-Aufrufer ein uninitialisiertes Array wünscht. Siehe auch [`undef`](@ref), ein Alias für `UndefInitializer()`.

# Beispiele

```julia-repl
julia> Array{Float64, 1}(UndefInitializer(), 3)
3-element Array{Float64, 1}:
 2.2752528595e-314
 2.202942107e-314
 2.275252907e-314
```
