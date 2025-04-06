```
setproperty!(value, name::Symbol, x)
setproperty!(value, name::Symbol, x, order::Symbol)
```

La sintaxis `a.b = c` llama a `setproperty!(a, :b, c)`. La sintaxis `@atomic order a.b = c` llama a `setproperty!(a, :b, c, :order)` y la sintaxis `@atomic a.b = c` llama a `setproperty!(a, :b, c, :sequentially_consistent)`.

!!! compat "Julia 1.8"
    `setproperty!` en módulos requiere al menos Julia 1.8.


Véase también [`setfield!`](@ref Core.setfield!), [`propertynames`](@ref Base.propertynames) y [`getproperty`](@ref Base.getproperty).
