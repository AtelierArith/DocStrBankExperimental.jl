```
redirect_stdin(f::Function, stream)
```

Ejecuta la función `f` mientras redirige [`stdin`](@ref) a `stream`. Al finalizar, [`stdin`](@ref) se restaura a su configuración anterior.
