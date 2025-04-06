```
swapglobal!(module::Module, name::Symbol, x, [order::Symbol=:monotonic])
```

Führen Sie atomar die Operationen aus, um gleichzeitig eine globale Variable zu lesen und zu setzen.

!!! compat "Julia 1.11"
    Diese Funktion erfordert Julia 1.11 oder höher.


Siehe auch [`swapproperty!`](@ref Base.swapproperty!) und [`setglobal!`](@ref).
