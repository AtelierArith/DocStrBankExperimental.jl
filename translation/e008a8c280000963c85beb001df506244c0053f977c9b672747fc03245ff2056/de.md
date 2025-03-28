```
indexin(a, b)
```

Gibt ein Array zurück, das den ersten Index in `b` für jeden Wert in `a` enthält, der ein Mitglied von `b` ist. Das Ausgabearray enthält `nothing`, wo immer `a` kein Mitglied von `b` ist.

Siehe auch: [`sortperm`](@ref), [`findfirst`](@ref).

# Beispiele

```jldoctest
julia> a = ['a', 'b', 'c', 'b', 'd', 'a'];

julia> b = ['a', 'b', 'c'];

julia> indexin(a, b)
6-element Vector{Union{Nothing, Int64}}:
 1
 2
 3
 2
  nothing
 1

julia> indexin(b, a)
3-element Vector{Union{Nothing, Int64}}:
 1
 2
 3
```
