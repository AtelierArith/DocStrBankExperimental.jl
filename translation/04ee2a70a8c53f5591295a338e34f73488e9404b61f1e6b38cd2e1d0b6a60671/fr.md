```
Core.memoryref_isassigned(::GenericMemoryRef, ordering::Symbol, boundscheck::Bool)
```

Renvoie si une valeur est stockée à l'`MemoryRef`, renvoyant faux si la `Memory` est vide. Voir [`isassigned(::Base.RefValue)`](@ref), [`Core.memoryrefget`](@ref). L'ordre de mémoire spécifié doit être compatible avec le paramètre `isatomic`.

!!! compat "Julia 1.11"
    Cette fonction nécessite Julia 1.11 ou une version ultérieure.

