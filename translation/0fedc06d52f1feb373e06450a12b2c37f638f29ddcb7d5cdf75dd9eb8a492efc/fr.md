```
isless(a::AbstractString, b::AbstractString) -> Bool
```

Testez si la chaîne `a` vient avant la chaîne `b` dans l'ordre alphabétique (techniquement, dans l'ordre lexicographique par les points de code Unicode).

# Exemples

```jldoctest
julia> isless("a", "b")
true

julia> isless("β", "α")
false

julia> isless("a", "a")
false
```
