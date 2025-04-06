```
lmul!(a::Number, B::AbstractArray)
```

스칼라 `a`로 배열 `B`를 스케일링하여 `B`를 제자리에서 덮어씁니다. 스칼라를 오른쪽에서 곱하려면 [`rmul!`](@ref)를 사용하세요. 스케일링 작업은 `a`와 `B`의 요소 간의 곱셈 [`*`](@ref)의 의미를 존중합니다. 특히, 이는 `NaN` 및 `±Inf`와 같은 비유한 숫자를 포함하는 곱셈에도 적용됩니다.

!!! compat "Julia 1.1"
    Julia 1.1 이전에는 `B`의 `NaN` 및 `±Inf` 항목이 일관되지 않게 처리되었습니다.


# 예제

```jldoctest
julia> B = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> lmul!(2, B)
2×2 Matrix{Int64}:
 2  4
 6  8

julia> lmul!(0.0, [Inf])
1-element Vector{Float64}:
 NaN
```
