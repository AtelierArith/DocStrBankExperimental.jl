```
Sys.isdragonfly([os])
```

Prédicat pour tester si le système d'exploitation est un dérivé de DragonFly BSD. Voir la documentation dans [Handling Operating System Variation](@ref).

!!! note
    Ne pas confondre avec `Sys.isbsd()`, qui est `true` sur DragonFly mais aussi sur d'autres systèmes basés sur BSD. `Sys.isdragonfly()` fait référence uniquement à DragonFly.


!!! compat "Julia 1.1"
    Cette fonction nécessite au moins Julia 1.1.

