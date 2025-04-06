```
uppercase(c::AbstractChar)
```

Convertir `c` en majuscule.

Voir aussi [`lowercase`](@ref), [`titlecase`](@ref).

# Exemples

```jldoctest
julia> uppercase('a')
'A': ASCII/Unicode U+0041 (catégorie Lu: Lettre, majuscule)

julia> uppercase('ê')
'Ê': Unicode U+00CA (catégorie Lu: Lettre, majuscule)
```
