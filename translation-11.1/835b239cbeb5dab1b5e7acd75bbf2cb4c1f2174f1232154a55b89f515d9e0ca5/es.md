```
exit_on_sigint(on::Bool)
```

Establece la bandera `exit_on_sigint` del tiempo de ejecución de julia. Si es `false`, Ctrl-C (SIGINT) se puede capturar como [`InterruptException`](@ref) en un bloque `try`. Este es el comportamiento predeterminado en REPL, cualquier código ejecutado a través de `-e` y `-E` y en un script de Julia ejecutado con la opción `-i`.

Si es `true`, `InterruptException` no se lanza con Ctrl-C. Ejecutar código ante tal evento requiere [`atexit`](@ref). Este es el comportamiento predeterminado en un script de Julia ejecutado sin la opción `-i`.

!!! compat "Julia 1.5"
    La función `exit_on_sigint` requiere al menos Julia 1.5.

