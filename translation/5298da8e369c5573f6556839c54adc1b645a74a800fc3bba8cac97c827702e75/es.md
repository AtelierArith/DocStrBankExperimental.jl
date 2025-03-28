```
open(f::Function, command, args...; kwargs...)
```

Similar a `open(command, args...; kwargs...)`, pero llama a `f(stream)` en el flujo de proceso resultante, luego cierra el flujo de entrada y espera a que el proceso se complete. Devuelve el valor devuelto por `f` en caso de éxito. Lanza un error si el proceso falla, o si el proceso intenta imprimir algo en stdout.
