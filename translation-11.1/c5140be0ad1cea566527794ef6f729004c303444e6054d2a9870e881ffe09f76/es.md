```
Sys.isfreebsd([os])
```

Predicado para probar si el sistema operativo es un derivado de FreeBSD. Consulta la documentación en [Handling Operating System Variation](@ref).

!!! nota
    No debe confundirse con `Sys.isbsd()`, que es `true` en FreeBSD pero también en otros sistemas basados en BSD. `Sys.isfreebsd()` se refiere solo a FreeBSD.


!!! compat "Julia 1.1"
    Esta función requiere al menos Julia 1.1.

