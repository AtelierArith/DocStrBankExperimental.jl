```
lowercase(c::AbstractChar)
```

Convertir `c` en minuscule.

Voir aussi [`uppercase`](@ref), [`titlecase`](@ref).

# Exemples

```jldoctest
julia> lowercase('A')
'a': ASCII/Unicode U+0061 (catégorie Ll: Lettre, minuscule)

julia> lowercase('Ö')
'ö': Unicode U+00F6 (catégorie Ll: Lettre, minuscule)
```
