```
rstrip([pred=isspace,] str::AbstractString) -> SubString
rstrip(str::AbstractString, chars) -> SubString
```

Elimina los caracteres finales de `str`, ya sea aquellos especificados por `chars` o aquellos para los cuales la función `pred` devuelve `true`.

El comportamiento predeterminado es eliminar los espacios en blanco y delimitadores finales: consulta [`isspace`](@ref) para obtener detalles precisos.

El argumento opcional `chars` especifica qué caracteres eliminar: puede ser un solo carácter, o un vector o conjunto de caracteres.

Consulta también [`strip`](@ref) y [`lstrip`](@ref).

# Ejemplos

```jldoctest
julia> a = rpad("March", 20)
"March               "

julia> rstrip(a)
"March"
```
