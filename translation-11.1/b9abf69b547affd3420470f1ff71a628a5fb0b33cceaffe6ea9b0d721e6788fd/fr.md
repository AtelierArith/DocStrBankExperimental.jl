```
replaceglobal!(module::Module, name::Symbol, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
```

Effectuer atomiquement les opérations pour obtenir et conditionnellement définir une variable globale à une valeur donnée.

!!! compat "Julia 1.11"
    Cette fonction nécessite Julia 1.11 ou une version ultérieure.


Voir aussi [`replaceproperty!`](@ref Base.replaceproperty!) et [`setglobal!`](@ref).
