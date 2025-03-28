```
copy!(dst, src) -> dst
```

Copia en su lugar [`copy`](@ref) de `src` a `dst`, descartando cualquier elemento preexistente en `dst`. Si `dst` y `src` son del mismo tipo, `dst == src` debería ser cierto después de la llamada. Si `dst` y `src` son arreglos multidimensionales, deben tener los mismos [`axes`](@ref).

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.


Véase también [`copyto!`](@ref).

!!! compat "Julia 1.1"
    Este método requiere al menos Julia 1.1. En Julia 1.0, este método está disponible en la biblioteca estándar `Future` como `Future.copy!`.

