```
swapproperty!(x, f::Symbol, v, order::Symbol=:not_atomic)
```

Die Syntax `@atomic a.b, _ = c, a.b` gibt `(c, swapproperty!(a, :b, c, :sequentially_consistent))` zurück, wobei es einen `getproperty`-Ausdruck geben muss, der auf beiden Seiten gemeinsam ist.

Siehe auch [`swapfield!`](@ref Core.swapfield!) und [`setproperty!`](@ref Base.setproperty!).
