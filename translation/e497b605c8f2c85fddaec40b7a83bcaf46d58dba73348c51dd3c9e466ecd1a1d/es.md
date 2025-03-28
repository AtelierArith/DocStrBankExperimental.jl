```
uppercasefirst(s::AbstractString) -> String
```

Devuelve `s` con el primer carácter convertido a mayúsculas (técnicamente "título" para Unicode). Consulta también [`titlecase`](@ref) para capitalizar el primer carácter de cada palabra en `s`.

Consulta también [`lowercasefirst`](@ref), [`uppercase`](@ref), [`lowercase`](@ref), [`titlecase`](@ref).

# Ejemplos

```jldoctest
julia> uppercasefirst("python")
"Python"
```
