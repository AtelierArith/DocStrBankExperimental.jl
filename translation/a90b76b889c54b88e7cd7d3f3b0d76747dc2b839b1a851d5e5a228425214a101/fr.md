```
peel(iter)
```

Renvoie le premier élément et un itérateur sur les éléments restants.

Si l'itérateur est vide, renvoie `nothing` (comme `iterate`).

!!! compat "Julia 1.7"
    Les versions antérieures lancent une BoundsError si l'itérateur est vide.


Voir aussi : [`Iterators.drop`](@ref), [`Iterators.take`](@ref).

# Exemples

```jldoctest
julia> (a, rest) = Iterators.peel("abc");

julia> a
'a': ASCII/Unicode U+0061 (catégorie Ll : Lettre, minuscule)

julia> collect(rest)
2-element Vector{Char}:
 'b': ASCII/Unicode U+0062 (catégorie Ll : Lettre, minuscule)
 'c': ASCII/Unicode U+0063 (catégorie Ll : Lettre, minuscule)
```
