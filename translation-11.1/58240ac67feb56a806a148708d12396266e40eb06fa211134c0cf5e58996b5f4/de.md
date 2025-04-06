```
setglobalonce!(module::Module, name::Symbol, value,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> success::Bool
```

Führen Sie atomar die Operationen aus, um eine globale Variable auf einen bestimmten Wert zu setzen, nur wenn sie zuvor nicht gesetzt war.

!!! compat "Julia 1.11"
    Diese Funktion erfordert Julia 1.11 oder höher.


Siehe auch [`setpropertyonce!`](@ref Base.setpropertyonce!) und [`setglobal!`](@ref).
