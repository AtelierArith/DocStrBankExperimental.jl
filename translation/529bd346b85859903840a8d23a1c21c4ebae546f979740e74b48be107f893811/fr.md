```
==(a::AbstractString, b::AbstractString) -> Bool
```

Testez si deux chaînes de caractères sont égales caractère par caractère (techniquement, point de code Unicode par point de code). Si l'une des chaînes est un [`AnnotatedString`](@ref), les propriétés de la chaîne doivent également correspondre.

# Exemples

```jldoctest
julia> "abc" == "abc"
true

julia> "abc" == "αβγ"
false
```
