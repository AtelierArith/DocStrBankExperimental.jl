```
titlecase(c::AbstractChar)
```

Convierte `c` a mayúsculas de título. Esto puede diferir de las mayúsculas para dígrafos, compara el ejemplo a continuación.

Véase también [`uppercase`](@ref), [`lowercase`](@ref).

# Ejemplos

```jldoctest
julia> titlecase('a')
'A': ASCII/Unicode U+0041 (categoría Lu: Letra, mayúscula)

julia> titlecase('ǆ')
'ǅ': Unicode U+01C5 (categoría Lt: Letra, mayúscula de título)

julia> uppercase('ǆ')
'Ǆ': Unicode U+01C4 (categoría Lu: Letra, mayúscula)
```
