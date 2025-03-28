```
Sys.isbsd([os])
```

Prédicat pour tester si le système d'exploitation est un dérivé de BSD. Voir la documentation dans [Handling Operating System Variation](@ref).

!!! note
    Le noyau Darwin descend de BSD, ce qui signifie que `Sys.isbsd()` est `true` sur les systèmes macOS. Pour exclure macOS d'un prédicat, utilisez `Sys.isbsd() && !Sys.isapple()`.

