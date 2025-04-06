```
logabsdet(M)
```

행렬 행렬식의 절대값의 로그. `(log(abs(det(M))), sign(det(M)))`와 동등하지만, 정확도 및/또는 속도가 향상될 수 있습니다.

# 예제

```jldoctest
julia> A = [-1. 0.; 0. 1.]
2×2 Matrix{Float64}:
 -1.0  0.0
  0.0  1.0

julia> det(A)
-1.0

julia> logabsdet(A)
(0.0, -1.0)

julia> B = [2. 0.; 0. 1.]
2×2 Matrix{Float64}:
 2.0  0.0
 0.0  1.0

julia> det(B)
2.0

julia> logabsdet(B)
(0.6931471805599453, 1.0)
```
