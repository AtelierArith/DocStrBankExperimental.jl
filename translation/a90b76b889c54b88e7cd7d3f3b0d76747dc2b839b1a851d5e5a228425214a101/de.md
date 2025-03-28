```
peel(iter)
```

Gibt das erste Element und einen Iterator über die verbleibenden Elemente zurück.

Wenn der Iterator leer ist, wird `nothing` zurückgegeben (wie bei `iterate`).

!!! compat "Julia 1.7"
    Frühere Versionen werfen einen BoundsError, wenn der Iterator leer ist.


Siehe auch: [`Iterators.drop`](@ref), [`Iterators.take`](@ref).

# Beispiele

```jldoctest
julia> (a, rest) = Iterators.peel("abc");

julia> a
'a': ASCII/Unicode U+0061 (Kategorie Ll: Buchstabe, Kleinbuchstabe)

julia> collect(rest)
2-element Vector{Char}:
 'b': ASCII/Unicode U+0062 (Kategorie Ll: Buchstabe, Kleinbuchstabe)
 'c': ASCII/Unicode U+0063 (Kategorie Ll: Buchstabe, Kleinbuchstabe)
```
