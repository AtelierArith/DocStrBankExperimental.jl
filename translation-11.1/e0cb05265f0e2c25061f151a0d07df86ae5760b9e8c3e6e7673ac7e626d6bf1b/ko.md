```
cos(A::AbstractMatrix)
```

정사각형 행렬 `A`의 행렬 코사인을 계산합니다.

`A`가 대칭 또는 에르미트인 경우, 고유 분해([`eigen`](@ref))를 사용하여 코사인을 계산합니다. 그렇지 않으면, 코사인은 [`exp`](@ref)를 호출하여 결정됩니다.

# 예제

```jldoctest
julia> cos(fill(1.0, (2,2)))
2×2 Matrix{Float64}:
  0.291927  -0.708073
 -0.708073   0.291927
```
