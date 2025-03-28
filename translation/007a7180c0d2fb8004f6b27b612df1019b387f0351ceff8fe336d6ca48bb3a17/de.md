```
Core.memoryrefsetonce!(::GenericMemoryRef, value,
                       success_order::Symbol, fail_order::Symbol=success_order, boundscheck::Bool) -> success::Bool
```

Führen Sie atomar die Operationen aus, um einen `MemoryRef` auf einen bestimmten Wert zu setzen, nur wenn er zuvor nicht gesetzt war.

!!! compat "Julia 1.11"
    Diese Funktion erfordert Julia 1.11 oder höher.


Siehe auch [`setpropertyonce!`](@ref Base.replaceproperty!) und [`Core.memoryrefset!`](@ref).
