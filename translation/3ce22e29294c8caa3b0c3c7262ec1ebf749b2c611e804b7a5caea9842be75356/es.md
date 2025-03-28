```
findnext(pattern::AbstractString, string::AbstractString, start::Integer)
findnext(pattern::AbstractPattern, string::String, start::Integer)
```

Encuentra la siguiente ocurrencia de `pattern` en `string` comenzando en la posición `start`. `pattern` puede ser una cadena o una expresión regular, en cuyo caso `string` debe ser de tipo `String`.

El valor de retorno es un rango de índices donde se encuentra la secuencia coincidente, de modo que `s[findnext(x, s, i)] == x`:

`findnext("substring", string, i)` == `start:stop` tal que `string[start:stop] == "substring"` y `i <= start`, o `nothing` si no hay coincidencia.

# Ejemplos

```jldoctest
julia> findnext("z", "Hello to the world", 1) === nothing
true

julia> findnext("o", "Hello to the world", 6)
8:8

julia> findnext("Lang", "JuliaLang", 2)
6:9
```
