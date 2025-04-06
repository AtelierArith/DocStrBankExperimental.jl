```
lowercase(c::AbstractChar)
```

Convierte `c` a minúsculas.

Véase también [`uppercase`](@ref), [`titlecase`](@ref).

# Ejemplos

```jldoctest
julia> lowercase('A')
'a': ASCII/Unicode U+0061 (categoría Ll: Letra, minúscula)

julia> lowercase('Ö')
'ö': Unicode U+00F6 (categoría Ll: Letra, minúscula)
```
