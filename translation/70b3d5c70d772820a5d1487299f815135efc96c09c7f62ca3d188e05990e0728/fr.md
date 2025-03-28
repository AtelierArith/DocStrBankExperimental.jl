```
Sys.isnetbsd([os])
```

Prédicat pour tester si le système d'exploitation est un dérivé de NetBSD. Voir la documentation dans [Handling Operating System Variation](@ref).

!!! note
    Ne pas confondre avec `Sys.isbsd()`, qui est `true` sur NetBSD mais aussi sur d'autres systèmes basés sur BSD. `Sys.isnetbsd()` fait référence uniquement à NetBSD.


!!! compat "Julia 1.1"
    Cette fonction nécessite au moins Julia 1.1.

