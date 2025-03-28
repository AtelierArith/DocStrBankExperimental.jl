```
uppercase(c::AbstractChar)
```

Convierte `c` a mayúsculas.

Véase también [`lowercase`](@ref), [`titlecase`](@ref).

# Ejemplos

```jldoctest
julia> uppercase('a')
'A': ASCII/Unicode U+0041 (categoría Lu: Letra, mayúscula)

julia> uppercase('ê')
'Ê': Unicode U+00CA (categoría Lu: Letra, mayúscula)
```
