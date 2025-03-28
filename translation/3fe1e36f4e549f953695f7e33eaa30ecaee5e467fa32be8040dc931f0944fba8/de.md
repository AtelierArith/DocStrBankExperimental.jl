```
clamp!(array::AbstractArray, lo, hi)
```

Werte in `array` auf den angegebenen Bereich beschränken, in-place. Siehe auch [`clamp`](@ref).

!!! compat "Julia 1.3"
    `missing`-Einträge in `array` erfordern mindestens Julia 1.3.


# Beispiele

```jldoctest
julia> row = collect(-4:4)';

julia> clamp!(row, 0, Inf)
1×9 adjoint(::Vector{Int64}) mit eltype Int64:
 0  0  0  0  0  1  2  3  4

julia> clamp.((-4:4)', 0, Inf)
1×9 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0  1.0  2.0  3.0  4.0
```
