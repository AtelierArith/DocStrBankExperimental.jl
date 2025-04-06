```
ArgWrite = Union{AbstractString, AbstractCmd, IO}
```

El tipo `ArgWrite` es una unión de los tipos que la función `arg_write` sabe cómo convertir en manejadores de IO escribibles, excepto por `Nothing`, que `arg_write` maneja generando un archivo temporal. Consulta [`arg_write`](@ref) para más detalles.
