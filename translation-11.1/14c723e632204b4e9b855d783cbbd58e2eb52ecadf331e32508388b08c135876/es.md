```
tuple(xs...)
```

Construye una tupla de los objetos dados.

Véase también [`Tuple`](@ref), [`ntuple`](@ref), [`NamedTuple`](@ref).

# Ejemplos

```jldoctest
julia> tuple(1, 'b', pi)
(1, 'b', π)

julia> ans === (1, 'b', π)
true

julia> Tuple(Real[1, 2, pi])  # toma una colección
(1, 2, π)
```
