```
Core.memoryrefsetonce!(::GenericMemoryRef, value,
                       success_order::Symbol, fail_order::Symbol=success_order, boundscheck::Bool) -> success::Bool
```

Realiza atómicamente las operaciones para establecer un `MemoryRef` a un valor dado, solo si no se había establecido previamente.

!!! compat "Julia 1.11"
    Esta función requiere Julia 1.11 o posterior.


Véase también [`setpropertyonce!`](@ref Base.replaceproperty!) y [`Core.memoryrefset!`](@ref).
