```
Sys.isnetbsd([os])
```

Predicado para probar si el sistema operativo es un derivado de NetBSD. Consulta la documentación en [Handling Operating System Variation](@ref).

!!! nota
    No debe confundirse con `Sys.isbsd()`, que es `true` en NetBSD pero también en otros sistemas basados en BSD. `Sys.isnetbsd()` se refiere únicamente a NetBSD.


!!! compat "Julia 1.1"
    Esta función requiere al menos Julia 1.1.

