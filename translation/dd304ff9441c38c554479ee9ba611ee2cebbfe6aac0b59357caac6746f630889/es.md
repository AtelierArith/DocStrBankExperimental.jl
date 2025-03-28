```
modifyglobal!(module::Module, name::Symbol, op, x, [order::Symbol=:monotonic]) -> Pair
```

Realiza de manera atómica las operaciones para obtener y establecer un global después de aplicar la función `op`.

!!! compat "Julia 1.11"
    Esta función requiere Julia 1.11 o posterior.


Véase también [`modifyproperty!`](@ref Base.modifyproperty!) y [`setglobal!`](@ref).
