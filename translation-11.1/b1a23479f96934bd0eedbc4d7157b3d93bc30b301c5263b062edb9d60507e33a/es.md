```
invokelatest(f, args...; kwargs...)
```

Llama a `f(args...; kwargs...)`, pero garantiza que se ejecutará el método más reciente de `f`. Esto es útil en circunstancias especializadas, por ejemplo, bucles de eventos de larga duración o funciones de devolución de llamada que pueden llamar a versiones obsoletas de una función `f`. (La desventaja es que `invokelatest` es algo más lento que llamar a `f` directamente, y el tipo del resultado no puede ser inferido por el compilador.)

!!! compat "Julia 1.9"
    Antes de Julia 1.9, esta función no se exportaba y se llamaba como `Base.invokelatest`.

