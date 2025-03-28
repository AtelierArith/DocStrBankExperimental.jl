```
Sys.isopenbsd([os])
```

Prédicat pour tester si le système d'exploitation est un dérivé d'OpenBSD. Voir la documentation dans [Handling Operating System Variation](@ref).

!!! note
    Ne pas confondre avec `Sys.isbsd()`, qui est `true` sur OpenBSD mais aussi sur d'autres systèmes basés sur BSD. `Sys.isopenbsd()` fait référence uniquement à OpenBSD.


!!! compat "Julia 1.1"
    Cette fonction nécessite au moins Julia 1.1.

