```
chomp(s::AbstractString) -> SubString
```

Supprime une seule nouvelle ligne à la fin d'une chaîne.

Voir aussi [`chop`](@ref).

# Exemples

```jldoctest
julia> chomp("Hello\n")
"Hello"
```
