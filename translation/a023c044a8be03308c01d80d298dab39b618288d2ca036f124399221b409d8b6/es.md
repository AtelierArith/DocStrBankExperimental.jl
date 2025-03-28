```
swapglobal!(module::Module, name::Symbol, x, [order::Symbol=:monotonic])
```

Realiza atómicamente las operaciones para obtener y establecer simultáneamente un global.

!!! compat "Julia 1.11"
    Esta función requiere Julia 1.11 o posterior.


Véase también [`swapproperty!`](@ref Base.swapproperty!) y [`setglobal!`](@ref).
