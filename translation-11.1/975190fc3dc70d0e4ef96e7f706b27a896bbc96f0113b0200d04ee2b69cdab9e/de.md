```
setproperty!(value, name::Symbol, x)
setproperty!(value, name::Symbol, x, order::Symbol)
```

Die Syntax `a.b = c` ruft `setproperty!(a, :b, c)` auf. Die Syntax `@atomic order a.b = c` ruft `setproperty!(a, :b, c, :order)` auf und die Syntax `@atomic a.b = c` ruft `setproperty!(a, :b, c, :sequentially_consistent)` auf.

!!! compat "Julia 1.8"
    `setproperty!` für Module erfordert mindestens Julia 1.8.


Siehe auch [`setfield!`](@ref Core.setfield!), [`propertynames`](@ref Base.propertynames) und [`getproperty`](@ref Base.getproperty).
