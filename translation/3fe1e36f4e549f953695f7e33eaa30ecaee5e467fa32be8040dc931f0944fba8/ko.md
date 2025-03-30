```
clamp!(array::AbstractArray, lo, hi)
```

`array`의 값을 지정된 범위로 제한합니다. 제자리에서 수행됩니다. [`clamp`](@ref)도 참조하세요.

!!! compat "Julia 1.3"
    `array`의 `missing` 항목은 최소한 Julia 1.3이 필요합니다.


# 예제

```jldoctest
julia> row = collect(-4:4)';

julia> clamp!(row, 0, Inf)
1×9 adjoint(::Vector{Int64}) with eltype Int64:
 0  0  0  0  0  1  2  3  4

julia> clamp.((-4:4)', 0, Inf)
1×9 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0  1.0  2.0  3.0  4.0
```
