```
modifyglobal!(module::Module, name::Symbol, op, x, [order::Symbol=:monotonic]) -> Pair
```

Führen Sie atomar die Operationen aus, um eine globale Variable zu lesen und zu setzen, nachdem die Funktion `op` angewendet wurde.

!!! compat "Julia 1.11"
    Diese Funktion erfordert Julia 1.11 oder höher.


Siehe auch [`modifyproperty!`](@ref Base.modifyproperty!) und [`setglobal!`](@ref).
