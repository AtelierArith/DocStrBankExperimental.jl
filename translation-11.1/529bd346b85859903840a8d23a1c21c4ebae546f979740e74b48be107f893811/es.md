```
==(a::AbstractString, b::AbstractString) -> Bool
```

Prueba si dos cadenas son iguales carácter por carácter (técnicamente, punto de código Unicode por punto de código). Si alguna de las cadenas es un [`AnnotatedString`](@ref), las propiedades de la cadena también deben coincidir.

# Ejemplos

```jldoctest
julia> "abc" == "abc"
true

julia> "abc" == "αβγ"
false
```
