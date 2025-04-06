```
peel(iter)
```

Devuelve el primer elemento y un iterador sobre los elementos restantes.

Si el iterador está vacío, devuelve `nothing` (como `iterate`).

!!! compat "Julia 1.7"
    Las versiones anteriores lanzan un BoundsError si el iterador está vacío.


Véase también: [`Iterators.drop`](@ref), [`Iterators.take`](@ref).

# Ejemplos

```jldoctest
julia> (a, rest) = Iterators.peel("abc");

julia> a
'a': ASCII/Unicode U+0061 (categoría Ll: Letra, minúscula)

julia> collect(rest)
2-element Vector{Char}:
 'b': ASCII/Unicode U+0062 (categoría Ll: Letra, minúscula)
 'c': ASCII/Unicode U+0063 (categoría Ll: Letra, minúscula)
```
