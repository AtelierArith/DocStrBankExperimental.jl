```
modifyglobal!(module::Module, name::Symbol, op, x, [order::Symbol=:monotonic]) -> Pair
```

Effectuer atomiquement les opérations pour obtenir et définir un global après avoir appliqué la fonction `op`.

!!! compat "Julia 1.11"
    Cette fonction nécessite Julia 1.11 ou une version ultérieure.


Voir aussi [`modifyproperty!`](@ref Base.modifyproperty!) et [`setglobal!`](@ref).
