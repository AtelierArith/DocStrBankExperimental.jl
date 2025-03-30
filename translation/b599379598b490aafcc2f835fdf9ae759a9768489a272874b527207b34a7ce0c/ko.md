```
sincos(A::AbstractMatrix)
```

정사각 행렬 `A`의 행렬 사인과 코사인을 계산합니다.

# 예제

```jldoctest
julia> S, C = sincos(fill(1.0, (2,2)));

julia> S
2×2 Matrix{Float64}:
 0.454649  0.454649
 0.454649  0.454649

julia> C
2×2 Matrix{Float64}:
  0.291927  -0.708073
 -0.708073   0.291927
```
