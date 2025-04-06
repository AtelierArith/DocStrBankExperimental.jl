```
findprev(pattern::AbstractString, string::AbstractString, start::Integer)
```

Encuentra la ocurrencia anterior de `pattern` en `string` comenzando en la posición `start`.

El valor de retorno es un rango de índices donde se encuentra la secuencia coincidente, de modo que `s[findprev(x, s, i)] == x`:

`findprev("substring", string, i)` == `start:stop` tal que `string[start:stop] == "substring"` y `stop <= i`, o `nothing` si no hay coincidencia.

# Ejemplos

```jldoctest
julia> findprev("z", "Hello to the world", 18) === nothing
true

julia> findprev("o", "Hello to the world", 18)
15:15

julia> findprev("Julia", "JuliaLang", 6)
1:5
```
