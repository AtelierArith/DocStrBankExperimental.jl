```
Core.memoryrefreplace!(::GenericMemoryRef, expected, desired,
                       success_order::Symbol, fail_order::Symbol=success_order, boundscheck::Bool) -> (; old, success::Bool)
```

Realiza de manera atómica las operaciones para obtener y establecer condicionalmente un valor de `MemoryRef`.

!!! compat "Julia 1.11"
    Esta función requiere Julia 1.11 o posterior.


Véase también [`replaceproperty!`](@ref Base.replaceproperty!) y [`Core.memoryrefset!`](@ref).
