```
parentindices(A)
```

Gibt die Indizes im [`parent`](@ref) zurück, die der Ansicht `A` entsprechen.

# Beispiele

```jldoctest
julia> A = [1 2; 3 4];

julia> V = view(A, 1, :)
2-element view(::Matrix{Int64}, 1, :) mit eltype Int64:
 1
 2

julia> parentindices(V)
(1, Base.Slice(Base.OneTo(2)))
```
