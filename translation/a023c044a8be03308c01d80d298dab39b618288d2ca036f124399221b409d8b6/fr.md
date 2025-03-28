```
swapglobal!(module::Module, name::Symbol, x, [order::Symbol=:monotonic])
```

Effectuer atomiquement les opérations pour obtenir et définir simultanément un global.

!!! compat "Julia 1.11"
    Cette fonction nécessite Julia 1.11 ou une version ultérieure.


Voir aussi [`swapproperty!`](@ref Base.swapproperty!) et [`setglobal!`](@ref).
