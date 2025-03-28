```
SubString(s::AbstractString, i::Integer, j::Integer=lastindex(s))
SubString(s::AbstractString, r::UnitRange{<:Integer})
```

Comme [`getindex`](@ref), mais renvoie une vue dans la chaîne parente `s` dans la plage `i:j` ou `r` respectivement au lieu de faire une copie.

Le macro [`@views`](@ref) convertit toutes les tranches de chaînes `s[i:j]` en sous-chaînes `SubString(s, i, j)` dans un bloc de code.

# Exemples

```jldoctest
julia> SubString("abc", 1, 2)
"ab"

julia> SubString("abc", 1:2)
"ab"

julia> SubString("abc", 2)
"bc"
```
