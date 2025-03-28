```
Core.memoryrefreplace!(::GenericMemoryRef, expected, desired,
                       success_order::Symbol, fail_order::Symbol=success_order, boundscheck::Bool) -> (; old, success::Bool)
```

Führen Sie atomar die Operationen aus, um einen `MemoryRef`-Wert zu erhalten und bedingt zu setzen.

!!! compat "Julia 1.11"
    Diese Funktion erfordert Julia 1.11 oder höher.


Siehe auch [`replaceproperty!`](@ref Base.replaceproperty!) und [`Core.memoryrefset!`](@ref).
