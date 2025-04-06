```
redirect_stdout(f::Function, stream)
```

Ejecuta la función `f` mientras rediriges [`stdout`](@ref) a `stream`. Al finalizar, [`stdout`](@ref) se restaura a su configuración anterior.
