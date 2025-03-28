```
lstrip([pred=isspace,] str::AbstractString) -> SubString
lstrip(str::AbstractString, chars) -> SubString
```

Elimina los caracteres iniciales de `str`, ya sea aquellos especificados por `chars` o aquellos para los cuales la función `pred` devuelve `true`.

El comportamiento predeterminado es eliminar los espacios en blanco y los delimitadores iniciales: consulta [`isspace`](@ref) para obtener detalles precisos.

El argumento opcional `chars` especifica qué caracteres eliminar: puede ser un solo carácter, o un vector o conjunto de caracteres.

Consulta también [`strip`](@ref) y [`rstrip`](@ref).

# Ejemplos

```jldoctest
julia> a = lpad("March", 20)
"               March"

julia> lstrip(a)
"March"
```
