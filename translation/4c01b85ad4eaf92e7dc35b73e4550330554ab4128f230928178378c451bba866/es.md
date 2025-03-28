```
InterruptException()
```

El proceso fue detenido por una interrupción del terminal (CTRL+C).

Tenga en cuenta que, en un script de Julia iniciado sin la opción `-i` (interactiva), `InterruptException` no se lanza por defecto. Llamar a [`Base.exit_on_sigint(false)`](@ref Base.exit_on_sigint) en el script puede recuperar el comportamiento del REPL. Alternativamente, un script de Julia se puede iniciar con

```sh
julia -e "include(popfirst!(ARGS))" script.jl
```

para permitir que `InterruptException` se lance por CTRL+C durante la ejecución.
