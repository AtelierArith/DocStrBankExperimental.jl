```
Sys.isfreebsd([os])
```

Prédicat pour tester si le système d'exploitation est un dérivé de FreeBSD. Voir la documentation dans [Handling Operating System Variation](@ref).

!!! note
    Ne pas confondre avec `Sys.isbsd()`, qui est `true` sur FreeBSD mais aussi sur d'autres systèmes basés sur BSD. `Sys.isfreebsd()` fait référence uniquement à FreeBSD.


!!! compat "Julia 1.1"
    Cette fonction nécessite au moins Julia 1.1.

