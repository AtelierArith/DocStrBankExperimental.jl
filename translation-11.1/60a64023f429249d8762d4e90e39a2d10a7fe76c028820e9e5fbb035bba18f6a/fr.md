```
titlecase(c::AbstractChar)
```

Convertir `c` en casse de titre. Cela peut différer de la casse supérieure pour les digraphes, comparez l'exemple ci-dessous.

Voir aussi [`uppercase`](@ref), [`lowercase`](@ref).

# Exemples

```jldoctest
julia> titlecase('a')
'A': ASCII/Unicode U+0041 (catégorie Lu: Lettre, majuscule)

julia> titlecase('ǆ')
'ǅ': Unicode U+01C5 (catégorie Lt: Lettre, casse de titre)

julia> uppercase('ǆ')
'Ǆ': Unicode U+01C4 (catégorie Lu: Lettre, majuscule)
```
