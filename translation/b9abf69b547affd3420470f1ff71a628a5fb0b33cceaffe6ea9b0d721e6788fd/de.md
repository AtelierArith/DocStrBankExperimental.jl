```
replaceglobal!(module::Module, name::Symbol, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
```

Führen Sie atomar die Operationen aus, um eine globale Variable zu erhalten und bedingt auf einen bestimmten Wert zu setzen.

!!! compat "Julia 1.11"
    Diese Funktion erfordert Julia 1.11 oder höher.


Siehe auch [`replaceproperty!`](@ref Base.replaceproperty!) und [`setglobal!`](@ref).
