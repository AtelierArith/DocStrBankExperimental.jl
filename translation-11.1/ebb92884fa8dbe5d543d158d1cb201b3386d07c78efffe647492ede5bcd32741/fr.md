```
match(r::Regex, s::AbstractString[, idx::Integer[, addopts]])
```

Recherchez la première correspondance de l'expression régulière `r` dans `s` et renvoyez un objet [`RegexMatch`](@ref) contenant la correspondance, ou rien si la correspondance a échoué. La sous-chaîne correspondante peut être récupérée en accédant à `m.match` et les séquences capturées peuvent être récupérées en accédant à `m.captures`. L'argument optionnel `idx` spécifie un index à partir duquel commencer la recherche.

# Exemples

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
