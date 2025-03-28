```
uppercasefirst(s::AbstractString) -> String
```

Retourne `s` avec le premier caractère converti en majuscule (techniquement "case de titre" pour Unicode). Voir aussi [`titlecase`](@ref) pour mettre en majuscule le premier caractère de chaque mot dans `s`.

Voir aussi [`lowercasefirst`](@ref), [`uppercase`](@ref), [`lowercase`](@ref), [`titlecase`](@ref).

# Exemples

```jldoctest
julia> uppercasefirst("python")
"Python"
```
