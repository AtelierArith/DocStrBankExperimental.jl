```
peel(iter)
```

İlk öğeyi ve kalan öğeler üzerinde bir iteratör döndürür.

Eğer iteratör boşsa `nothing` döner (tıpkı `iterate` gibi).

!!! compat "Julia 1.7"
    Önceki sürümler, iteratör boşsa bir BoundsError fırlatır.


Ayrıca bakınız: [`Iterators.drop`](@ref), [`Iterators.take`](@ref).

# Örnekler

```jldoctest
julia> (a, rest) = Iterators.peel("abc");

julia> a
'a': ASCII/Unicode U+0061 (kategori Ll: Harf, küçük)

julia> collect(rest)
2-element Vector{Char}:
 'b': ASCII/Unicode U+0062 (kategori Ll: Harf, küçük)
 'c': ASCII/Unicode U+0063 (kategori Ll: Harf, küçük)
```
