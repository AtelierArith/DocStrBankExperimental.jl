```
redirect_stderr(f::Function, stream)
```

Ejecuta la función `f` mientras redirige [`stderr`](@ref) a `stream`. Al finalizar, [`stderr`](@ref) se restaura a su configuración anterior.
