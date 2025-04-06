```
Core.memoryrefsetonce!(::GenericMemoryRef, value,
                       success_order::Symbol, fail_order::Symbol=success_order, boundscheck::Bool) -> success::Bool
```

Atomik olarak, daha önce ayarlanmamışsa bir `MemoryRef`'i verilen bir değere ayarlamak için işlemleri gerçekleştirin.

!!! compat "Julia 1.11"
    Bu işlev Julia 1.11 veya daha yenisini gerektirir.


Ayrıca bkz. [`setpropertyonce!`](@ref Base.replaceproperty!) ve [`Core.memoryrefset!`](@ref).
