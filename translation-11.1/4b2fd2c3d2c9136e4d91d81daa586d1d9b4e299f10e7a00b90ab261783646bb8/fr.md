```
swapproperty!(x, f::Symbol, v, order::Symbol=:not_atomic)
```

La syntaxe `@atomic a.b, _ = c, a.b` renvoie `(c, swapproperty!(a, :b, c, :sequentially_consistent))`, où il doit y avoir une expression `getproperty` commune aux deux côtés.

Voir aussi [`swapfield!`](@ref Core.swapfield!) et [`setproperty!`](@ref Base.setproperty!).
