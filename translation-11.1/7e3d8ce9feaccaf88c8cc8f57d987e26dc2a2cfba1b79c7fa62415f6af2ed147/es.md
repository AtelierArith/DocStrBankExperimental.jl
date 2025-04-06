```
Sys.isbsd([os])
```

Predicado para probar si el sistema operativo es un derivado de BSD. Consulta la documentación en [Handling Operating System Variation](@ref).

!!! note
    El núcleo de Darwin desciende de BSD, lo que significa que `Sys.isbsd()` es `true` en sistemas macOS. Para excluir macOS de un predicado, usa `Sys.isbsd() && !Sys.isapple()`.

