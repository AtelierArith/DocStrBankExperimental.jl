```
takewhile(pred, iter)
```

Ein Iterator, der Elemente aus `iter` generiert, solange die Bedingung `pred` wahr ist, danach werden alle Elemente verworfen.

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

julia> collect(Iterators.takewhile(<(3),s))
2-element Vector{Int64}:
 1
 2
```
