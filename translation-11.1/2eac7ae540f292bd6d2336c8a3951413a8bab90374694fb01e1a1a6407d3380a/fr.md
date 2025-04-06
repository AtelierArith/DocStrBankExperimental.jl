```
occursin(needle::Union{AbstractString,AbstractPattern,AbstractChar}, haystack::AbstractString)
```

Détermine si le premier argument est une sous-chaîne du second. Si `needle` est une expression régulière, vérifie si `haystack` contient une correspondance.

# Exemples

```jldoctest
julia> occursin("Julia", "JuliaLang is pretty cool!")
true

julia> occursin('a', "JuliaLang is pretty cool!")
true

julia> occursin(r"a.a", "aba")
true

julia> occursin(r"a.a", "abba")
false
```

Voir aussi [`contains`](@ref).
