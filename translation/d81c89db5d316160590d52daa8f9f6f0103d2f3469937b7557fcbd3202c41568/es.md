```
strip([pred=isspace,] str::AbstractString) -> SubString
strip(str::AbstractString, chars) -> SubString
```

Elimina los caracteres de inicio y fin de `str`, ya sea aquellos especificados por `chars` o aquellos para los cuales la función `pred` devuelve `true`.

El comportamiento predeterminado es eliminar los espacios en blanco y delimitadores de inicio y fin: consulta [`isspace`](@ref) para obtener detalles precisos.

El argumento opcional `chars` especifica qué caracteres eliminar: puede ser un solo carácter, un vector o un conjunto de caracteres.

Consulta también [`lstrip`](@ref) y [`rstrip`](@ref).

!!! compat "Julia 1.2"
    El método que acepta una función de predicado requiere Julia 1.2 o posterior.


# Ejemplos

```jldoctest
julia> strip("{3, 5}\n", ['{', '}', '\n'])
"3, 5"
```
