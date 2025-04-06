```
rmul!(A::AbstractArray, b::Number)
```

배열 `A`를 스칼라 `b`로 스케일링하여 `A`를 제자리에서 덮어씁니다. 스칼라를 왼쪽에서 곱하려면 [`lmul!`](@ref)를 사용하세요. 스케일링 작업은 `A`의 요소와 `b` 사이의 곱셈 [`*`](@ref)의 의미를 존중합니다. 특히, 이는 `NaN` 및 `±Inf`와 같은 비유한 숫자를 포함하는 곱셈에도 적용됩니다.

!!! compat "Julia 1.1"
    Julia 1.1 이전에는 `A`의 `NaN` 및 `±Inf` 항목이 일관되지 않게 처리되었습니다.


# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rmul!(A, 2)
2×2 Matrix{Int64}:
 2  4
 6  8

julia> rmul!([NaN], 0.0)
1-element Vector{Float64}:
 NaN
```
