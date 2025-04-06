```
setproperty!(value, name::Symbol, x)
setproperty!(value, name::Symbol, x, order::Symbol)
```

La syntaxe `a.b = c` appelle `setproperty!(a, :b, c)`. La syntaxe `@atomic order a.b = c` appelle `setproperty!(a, :b, c, :order)` et la syntaxe `@atomic a.b = c` appelle `setproperty!(a, :b, c, :sequentially_consistent)`.

!!! compat "Julia 1.8"
    `setproperty!` sur les modules nécessite au moins Julia 1.8.


Voir aussi [`setfield!`](@ref Core.setfield!), [`propertynames`](@ref Base.propertynames) et [`getproperty`](@ref Base.getproperty).
