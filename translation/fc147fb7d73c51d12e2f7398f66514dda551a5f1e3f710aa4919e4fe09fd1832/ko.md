```
ldiv!(a::Number, B::AbstractArray)
```

스칼라 `a`로 배열 `B`의 각 항목을 나누고 `B`를 제자리에서 덮어씁니다. 오른쪽에서 스칼라를 나누려면 [`rdiv!`](@ref)를 사용하세요.

# 예제

```jldoctest
julia> B = [1.0 2.0; 3.0 4.0]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> ldiv!(2.0, B)
2×2 Matrix{Float64}:
 0.5  1.0
 1.5  2.0
```
