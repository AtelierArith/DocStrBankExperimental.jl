```
ascii(s::AbstractString)
```

Convierte una cadena al tipo `String` y verifica que contenga solo datos ASCII, de lo contrario lanza un `ArgumentError` indicando la posición del primer byte no ASCII.

Véase también el predicado [`isascii`](@ref) para filtrar o reemplazar caracteres no ASCII.

# Ejemplos

```jldoctest
julia> ascii("abcdeγfgh")
ERROR: ArgumentError: invalid ASCII at index 6 in "abcdeγfgh"
Stacktrace:
[...]

julia> ascii("abcdefgh")
"abcdefgh"
```
