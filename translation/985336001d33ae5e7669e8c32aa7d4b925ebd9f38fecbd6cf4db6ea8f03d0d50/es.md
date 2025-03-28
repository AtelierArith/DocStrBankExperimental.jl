```
with_logger(function, logger)
```

Ejecuta `function`, dirigiendo todos los mensajes de registro a `logger`.

# Ejemplos

```julia
function test(x)
    @info "x = $x"
end

with_logger(logger) do
    test(1)
    test([1,2])
end
```
