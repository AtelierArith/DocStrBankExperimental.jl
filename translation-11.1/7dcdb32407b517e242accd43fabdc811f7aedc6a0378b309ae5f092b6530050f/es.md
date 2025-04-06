```
escape_string(str::AbstractString[, esc]; keep = ())::AbstractString
escape_string(io, str::AbstractString[, esc]; keep = ())::Nothing
```

Escapeo general de secuencias de escape tradicionales de C y Unicode. La primera forma devuelve la cadena escapada, la segunda imprime el resultado en `io`.

Las barras invertidas (`\`) se escapan con una doble barra invertida (`"\\"`). Los caracteres no imprimibles se escapan ya sea con sus códigos de escape estándar de C, `"\0"` para NUL (si es no ambiguo), el punto de código unicode (`"\u"` prefijo) o hex (`"\x"` prefijo).

El argumento opcional `esc` especifica cualquier carácter adicional que también debería ser escapado precediéndolo con una barra invertida (`"` también se escapa por defecto en la primera forma).

El argumento `keep` especifica una colección de caracteres que deben mantenerse tal como están. Tenga en cuenta que `esc` tiene prioridad aquí.

Véase también [`unescape_string`](@ref) para la operación inversa.

!!! compat "Julia 1.7"
    El argumento `keep` está disponible a partir de Julia 1.7.


# Ejemplos

```jldoctest
julia> escape_string("aaa\nbbb")
"aaa\\nbbb"

julia> escape_string("aaa\nbbb"; keep = '\n')
"aaa\nbbb"

julia> escape_string("\xfe\xff") # utf-8 inválido
"\\xfe\\xff"

julia> escape_string(string('\u2135','\0')) # no ambiguo
"ℵ\\0"

julia> escape_string(string('\u2135','\0','0')) # \0 sería ambiguo
"ℵ\\x000"
```
