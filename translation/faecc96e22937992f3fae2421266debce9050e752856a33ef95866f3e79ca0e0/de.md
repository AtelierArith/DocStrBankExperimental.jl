```
resize!(a::Vector, n::Integer) -> Vector
```

Ändert die Größe von `a`, um `n` Elemente zu enthalten. Wenn `n` kleiner als die aktuelle Länge der Sammlung ist, werden die ersten `n` Elemente beibehalten. Wenn `n` größer ist, ist nicht garantiert, dass die neuen Elemente initialisiert sind.

# Beispiele

```jldoctest
julia> resize!([6, 5, 4, 3, 2, 1], 3)
3-element Vector{Int64}:
 6
 5
 4

julia> a = resize!([6, 5, 4, 3, 2, 1], 8);

julia> length(a)
8

julia> a[1:6]
6-element Vector{Int64}:
 6
 5
 4
 3
 2
 1
```
