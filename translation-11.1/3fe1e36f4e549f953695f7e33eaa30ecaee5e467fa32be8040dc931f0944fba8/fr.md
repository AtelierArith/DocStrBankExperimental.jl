```
clamp!(array::AbstractArray, lo, hi)
```

Restreindre les valeurs dans `array` à la plage spécifiée, sur place. Voir aussi [`clamp`](@ref).

!!! compat "Julia 1.3"
    Les entrées `missing` dans `array` nécessitent au moins Julia 1.3.


# Exemples

```jldoctest
julia> row = collect(-4:4)';

julia> clamp!(row, 0, Inf)
1×9 adjoint(::Vector{Int64}) avec eltype Int64:
 0  0  0  0  0  1  2  3  4

julia> clamp.((-4:4)', 0, Inf)
1×9 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0  1.0  2.0  3.0  4.0
```
