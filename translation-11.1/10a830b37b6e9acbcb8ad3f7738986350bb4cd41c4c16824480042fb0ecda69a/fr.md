```
Core.memoryrefreplace!(::GenericMemoryRef, expected, desired,
                       success_order::Symbol, fail_order::Symbol=success_order, boundscheck::Bool) -> (; old, success::Bool)
```

Effectuer atomiquement les opérations pour obtenir et conditionnellement définir une valeur `MemoryRef`.

!!! compat "Julia 1.11"
    Cette fonction nécessite Julia 1.11 ou une version ultérieure.


Voir aussi [`replaceproperty!`](@ref Base.replaceproperty!) et [`Core.memoryrefset!`](@ref).
