```
Core.memoryrefswap!(::GenericMemoryRef, value, ordering::Symbol, boundscheck::Bool)
```

Führen Sie atomar die Operationen aus, um gleichzeitig einen `MemoryRef`-Wert zu erhalten und zu setzen.

!!! compat "Julia 1.11"
    Diese Funktion erfordert Julia 1.11 oder höher.


Siehe auch [`swapproperty!`](@ref Base.swapproperty!) und [`Core.memoryrefset!`](@ref).
