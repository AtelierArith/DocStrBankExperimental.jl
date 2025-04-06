```
isless(a::AbstractString, b::AbstractString) -> Bool
```

Prueba si la cadena `a` precede a la cadena `b` en orden alfabético (técnicamente, en orden lexicográfico por puntos de código Unicode).

# Ejemplos

```jldoctest
julia> isless("a", "b")
true

julia> isless("β", "α")
false

julia> isless("a", "a")
false
```
