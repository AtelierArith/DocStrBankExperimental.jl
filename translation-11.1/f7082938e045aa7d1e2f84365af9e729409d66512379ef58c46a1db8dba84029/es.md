```
SubString(s::AbstractString, i::Integer, j::Integer=lastindex(s))
SubString(s::AbstractString, r::UnitRange{<:Integer})
```

Como [`getindex`](@ref), pero devuelve una vista de la cadena principal `s` dentro del rango `i:j` o `r` respectivamente en lugar de hacer una copia.

El macro [`@views`](@ref) convierte cualquier rebanada de cadena `s[i:j]` en subcadenas `SubString(s, i, j)` en un bloque de código.

# Ejemplos

```jldoctest
julia> SubString("abc", 1, 2)
"ab"

julia> SubString("abc", 1:2)
"ab"

julia> SubString("abc", 2)
"bc"
```
