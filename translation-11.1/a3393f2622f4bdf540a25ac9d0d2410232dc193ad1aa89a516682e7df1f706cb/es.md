```
Sys.isdragonfly([os])
```

Predicado para probar si el sistema operativo es un derivado de DragonFly BSD. Consulta la documentación en [Handling Operating System Variation](@ref).

!!! nota
    No debe confundirse con `Sys.isbsd()`, que es `true` en DragonFly pero también en otros sistemas basados en BSD. `Sys.isdragonfly()` se refiere únicamente a DragonFly.


!!! compat "Julia 1.1"
    Esta función requiere al menos Julia 1.1.

