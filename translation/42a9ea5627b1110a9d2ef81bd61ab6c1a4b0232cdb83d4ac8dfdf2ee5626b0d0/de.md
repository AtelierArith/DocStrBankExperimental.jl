```
unique(itr)
```

Gibt ein Array zurück, das nur die einzigartigen Elemente der Sammlung `itr` enthält, wie durch [`isequal`](@ref) und [`hash`](@ref) bestimmt, in der Reihenfolge, in der das erste jedes Satzes von äquivalenten Elementen ursprünglich erscheint. Der Elementtyp des Eingangs wird beibehalten.

Siehe auch: [`unique!`](@ref), [`allunique`](@ref), [`allequal`](@ref).

# Beispiele

```jldoctest
julia> unique([1, 2, 6, 2])
3-element Vector{Int64}:
 1
 2
 6

julia> unique(Real[1, 1.0, 2])
2-element Vector{Real}:
 1
 2
```
