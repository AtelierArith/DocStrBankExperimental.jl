```
Core.memoryrefsetonce!(::GenericMemoryRef, value,
                       success_order::Symbol, fail_order::Symbol=success_order, boundscheck::Bool) -> success::Bool
```

Effectuer atomiquement les opérations pour définir un `MemoryRef` à une valeur donnée, uniquement s'il n'était pas précédemment défini.

!!! compat "Julia 1.11"
    Cette fonction nécessite Julia 1.11 ou une version ultérieure.


Voir aussi [`setpropertyonce!`](@ref Base.replaceproperty!) et [`Core.memoryrefset!`](@ref).
