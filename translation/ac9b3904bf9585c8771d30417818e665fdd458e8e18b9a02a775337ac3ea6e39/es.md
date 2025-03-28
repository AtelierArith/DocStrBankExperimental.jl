```
parentindices(A)
```

Devuelve los índices en el [`parent`](@ref) que corresponden a la vista `A`.

# Ejemplos

```jldoctest
julia> A = [1 2; 3 4];

julia> V = view(A, 1, :)
2-element view(::Matrix{Int64}, 1, :) con el tipo eltype Int64:
 1
 2

julia> parentindices(V)
(1, Base.Slice(Base.OneTo(2)))
```
