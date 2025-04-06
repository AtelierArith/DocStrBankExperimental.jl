```
findlast(ch::AbstractChar, string::AbstractString)
```

Finde das letzte Vorkommen des Zeichens `ch` in `string`.

!!! compat "Julia 1.3"
    Diese Methode erfordert mindestens Julia 1.3.


# Beispiele

```jldoctest
julia> findlast('p', "happy")
4

julia> findlast('z', "happy") === nothing
true
```
