```
vec(a::AbstractArray) -> AbstractVector
```

Formatiere das Array `a` als eindimensionalen Spaltenvektor. Gib `a` zurück, wenn es bereits ein `AbstractVector` ist. Das resultierende Array teilt sich die gleichen zugrunde liegenden Daten wie `a`, sodass es nur veränderbar ist, wenn `a` veränderbar ist, in welchem Fall die Modifikation des einen auch den anderen modifiziert.

# Beispiele

```jldoctest
julia> a = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> vec(a)
6-element Vector{Int64}:
 1
 4
 2
 5
 3
 6

julia> vec(1:3)
1:3
```

Siehe auch [`reshape`](@ref), [`dropdims`](@ref).
