```
Core.memoryrefswap!(::GenericMemoryRef, value, ordering::Symbol, boundscheck::Bool)
```

Realiza atómicamente las operaciones para obtener y establecer simultáneamente un valor de `MemoryRef`.

!!! compat "Julia 1.11"
    Esta función requiere Julia 1.11 o posterior.


Véase también [`swapproperty!`](@ref Base.swapproperty!) y [`Core.memoryrefset!`](@ref).
