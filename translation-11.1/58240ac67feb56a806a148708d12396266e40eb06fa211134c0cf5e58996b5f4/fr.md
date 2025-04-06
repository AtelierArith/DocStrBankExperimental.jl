```
setglobalonce!(module::Module, name::Symbol, value,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> success::Bool
```

Effectuer atomiquement les opérations pour définir une variable globale à une valeur donnée, uniquement si elle n'était pas précédemment définie.

!!! compat "Julia 1.11"
    Cette fonction nécessite Julia 1.11 ou une version ultérieure.


Voir aussi [`setpropertyonce!`](@ref Base.setpropertyonce!) et [`setglobal!`](@ref).
