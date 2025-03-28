```
swapproperty!(x, f::Symbol, v, order::Symbol=:not_atomic)
```

La sintaxis `@atomic a.b, _ = c, a.b` devuelve `(c, swapproperty!(a, :b, c, :sequentially_consistent))`, donde debe haber una expresión `getproperty` común a ambos lados.

Véase también [`swapfield!`](@ref Core.swapfield!) y [`setproperty!`](@ref Base.setproperty!).
