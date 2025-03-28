```
Core.memoryrefmodify!(::GenericMemoryRef, op, value, ordering::Symbol, boundscheck::Bool) -> Pair
```

Realiza de manera atómica las operaciones para obtener y establecer un valor de `MemoryRef` después de aplicar la función `op`.

!!! compat "Julia 1.11"
    Esta función requiere Julia 1.11 o posterior.


Véase también [`modifyproperty!`](@ref Base.modifyproperty!) y [`Core.memoryrefset!`](@ref).
