```
edit(path::AbstractString, line::Integer=0, column::Integer=0)
```

Edita un archivo o directorio proporcionando opcionalmente un número de línea para editar el archivo. Regresa al prompt de `julia` cuando salgas del editor. El editor se puede cambiar configurando `JULIA_EDITOR`, `VISUAL` o `EDITOR` como una variable de entorno.

!!! compat "Julia 1.9"
    El argumento `column` requiere al menos Julia 1.9.


Consulta también [`InteractiveUtils.define_editor`](@ref).
