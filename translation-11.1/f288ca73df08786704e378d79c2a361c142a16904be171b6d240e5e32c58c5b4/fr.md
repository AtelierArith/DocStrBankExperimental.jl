```
Core.memoryrefmodify!(::GenericMemoryRef, op, value, ordering::Symbol, boundscheck::Bool) -> Pair
```

Effectuer atomiquement les opérations pour obtenir et définir une valeur `MemoryRef` après avoir appliqué la fonction `op`.

!!! compat "Julia 1.11"
    Cette fonction nécessite Julia 1.11 ou une version ultérieure.


Voir aussi [`modifyproperty!`](@ref Base.modifyproperty!) et [`Core.memoryrefset!`](@ref).
