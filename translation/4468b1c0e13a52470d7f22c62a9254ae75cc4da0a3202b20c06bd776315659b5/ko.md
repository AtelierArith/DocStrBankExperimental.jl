```
rdiv!(A::AbstractArray, b::Number)
```

배열 `A`의 각 항목을 스칼라 `b`로 나누고 `A`를 제자리에서 덮어씁니다. 왼쪽에서 스칼라를 나누려면 [`ldiv!`](@ref)를 사용하세요.

# 예제

```jldoctest
julia> A = [1.0 2.0; 3.0 4.0]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> rdiv!(A, 2.0)
2×2 Matrix{Float64}:
 0.5  1.0
 1.5  2.0
```
