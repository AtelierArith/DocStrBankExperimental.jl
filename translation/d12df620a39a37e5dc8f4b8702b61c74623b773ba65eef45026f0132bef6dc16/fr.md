```
Core.memoryrefget(::GenericMemoryRef, ordering::Symbol, boundscheck::Bool)
```

Retourne la valeur stockée dans le `MemoryRef`, en lançant une `BoundsError` si la `Memory` est vide. Voir `ref[]`. L'ordre de mémoire spécifié doit être compatible avec le paramètre `isatomic`.

!!! compat "Julia 1.11"
    Cette fonction nécessite Julia 1.11 ou une version ultérieure.

