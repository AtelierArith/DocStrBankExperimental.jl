```
dropwhile(pred, iter)
```

Ein Iterator, der Elemente aus `iter` entfernt, solange das Prädikat `pred` wahr ist, und danach jedes Element zurückgibt.

!!! compat "Julia 1.4"
    Diese Funktion erfordert mindestens Julia 1.4.


# Beispiele

```jldoctest
julia> s = collect(1:5)
5-element Vector{Int64}:
 1
 2
 3
 4
 5

julia> collect(Iterators.dropwhile(<(3),s))
3-element Vector{Int64}:
 3
 4
 5
```
