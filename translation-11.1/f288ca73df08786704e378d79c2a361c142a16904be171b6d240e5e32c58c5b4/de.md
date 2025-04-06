```
Core.memoryrefmodify!(::GenericMemoryRef, op, value, ordering::Symbol, boundscheck::Bool) -> Pair
```

Führen Sie atomar die Operationen aus, um einen `MemoryRef`-Wert zu erhalten und zu setzen, nachdem die Funktion `op` angewendet wurde.

!!! compat "Julia 1.11"
    Diese Funktion erfordert Julia 1.11 oder höher.


Siehe auch [`modifyproperty!`](@ref Base.modifyproperty!) und [`Core.memoryrefset!`](@ref).
