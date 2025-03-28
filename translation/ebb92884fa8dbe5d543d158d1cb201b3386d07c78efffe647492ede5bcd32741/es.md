```
match(r::Regex, s::AbstractString[, idx::Integer[, addopts]])
```

Busca la primera coincidencia de la expresión regular `r` en `s` y devuelve un objeto [`RegexMatch`](@ref) que contiene la coincidencia, o nada si la coincidencia falló. La subcadena coincidente se puede recuperar accediendo a `m.match` y las secuencias capturadas se pueden recuperar accediendo a `m.captures`. El argumento opcional `idx` especifica un índice en el que comenzar la búsqueda.

# Ejemplos

```jldoctest
julia> rx = r"a(.)a"
r"a(.)a"

julia> m = match(rx, "cabac")
RegexMatch("aba", 1="b")

julia> m.captures
1-element Vector{Union{Nothing, SubString{String}}}:
 "b"

julia> m.match
"aba"

julia> match(rx, "cabac", 3) === nothing
true
```
