```
findnext(ch::AbstractChar, string::AbstractString, start::Integer)
```

Finde das nächste Vorkommen des Zeichens `ch` in `string`, beginnend an der Position `start`.

!!! compat "Julia 1.3"
    Diese Methode erfordert mindestens Julia 1.3.


# Beispiele

```jldoctest
julia> findnext('z', "Hello to the world", 1) === nothing
true

julia> findnext('o', "Hello to the world", 6)
8
```
