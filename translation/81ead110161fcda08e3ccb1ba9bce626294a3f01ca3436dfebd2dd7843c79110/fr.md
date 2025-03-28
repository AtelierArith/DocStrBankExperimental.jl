```
Core.memoryrefswap!(::GenericMemoryRef, value, ordering::Symbol, boundscheck::Bool)
```

Effectuer atomiquement les opérations pour obtenir et définir simultanément une valeur `MemoryRef`.

!!! compat "Julia 1.11"
    Cette fonction nécessite Julia 1.11 ou une version ultérieure.


Voir aussi [`swapproperty!`](@ref Base.swapproperty!) et [`Core.memoryrefset!`](@ref).
