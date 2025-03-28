```
Sys.isopenbsd([os])
```

Predicado para probar si el sistema operativo es un derivado de OpenBSD. Consulta la documentación en [Handling Operating System Variation](@ref).

!!! nota
    No debe confundirse con `Sys.isbsd()`, que es `true` en OpenBSD pero también en otros sistemas basados en BSD. `Sys.isopenbsd()` se refiere únicamente a OpenBSD.


!!! compat "Julia 1.1"
    Esta función requiere al menos Julia 1.1.

