```
replaceglobal!(module::Module, name::Symbol, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
```

Realiza atómicamente las operaciones para obtener y establecer condicionalmente un global a un valor dado.

!!! compat "Julia 1.11"
    Esta función requiere Julia 1.11 o posterior.


Véase también [`replaceproperty!`](@ref Base.replaceproperty!) y [`setglobal!`](@ref).
