```
Experimental.show_error_hints(io, ex, args...)
```

Invoquez tous les gestionnaires de [`Experimental.register_error_hint`](@ref) pour le type d'exception particulier `typeof(ex)`. `args` doit contenir tous les autres arguments attendus par le gestionnaire pour ce type.

!!! compat "Julia 1.5"
    Les indices d'erreur personnalisés sont disponibles depuis Julia 1.5.


!!! warning
    Cette interface est expérimentale et sujette à des modifications ou à une suppression sans préavis.

