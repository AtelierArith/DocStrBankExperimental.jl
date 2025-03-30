```
clamp!(array::AbstractArray, lo, hi)
```

`array` içindeki değerleri belirtilen aralıkla sınırlayın, yerinde. Ayrıca bkz. [`clamp`](@ref).

!!! compat "Julia 1.3"
    `array` içindeki `missing` girişleri en az Julia 1.3 gerektirir.


# Örnekler

```jldoctest
julia> row = collect(-4:4)';

julia> clamp!(row, 0, Inf)
1×9 adjoint(::Vector{Int64}) ile eltype Int64:
 0  0  0  0  0  1  2  3  4

julia> clamp.((-4:4)', 0, Inf)
1×9 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0  1.0  2.0  3.0  4.0
```
