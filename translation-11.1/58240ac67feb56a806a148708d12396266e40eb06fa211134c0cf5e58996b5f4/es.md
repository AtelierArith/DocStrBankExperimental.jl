```
setglobalonce!(module::Module, name::Symbol, value,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> success::Bool
```

Realiza atómicamente las operaciones para establecer un global a un valor dado, solo si no se había establecido previamente.

!!! compat "Julia 1.11"
    Esta función requiere Julia 1.11 o posterior.


Véase también [`setpropertyonce!`](@ref Base.setpropertyonce!) y [`setglobal!`](@ref).
