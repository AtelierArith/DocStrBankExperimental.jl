```
parentindices(A)
```

Retourne les indices dans le [`parent`](@ref) qui correspondent à la vue `A`.

# Exemples

```jldoctest
julia> A = [1 2; 3 4];

julia> V = view(A, 1, :)
2-element view(::Matrix{Int64}, 1, :) with eltype Int64:
 1
 2

julia> parentindices(V)
(1, Base.Slice(Base.OneTo(2)))
```
