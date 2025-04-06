```
keepat!(a::Vector, m::AbstractVector{Bool})
keepat!(a::BitVector, m::AbstractVector{Bool})
```

Die In-Place-Version der logischen Indizierung `a = a[m]`. Das heißt, `keepat!(a, m)` bei Vektoren gleicher Länge `a` und `m` entfernt alle Elemente aus `a`, für die `m` am entsprechenden Index `false` ist.

# Beispiele

```jldoctest
julia> a = [:a, :b, :c];

julia> keepat!(a, [true, false, true])
2-element Vector{Symbol}:
 :a
 :c

julia> a
2-element Vector{Symbol}:
 :a
 :c
```
