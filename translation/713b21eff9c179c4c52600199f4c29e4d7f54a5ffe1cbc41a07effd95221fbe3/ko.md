```
A / B
```

행렬 오른쪽 나누기: `A / B`는 `(B' \ A')'`와 동등하며, 여기서 [`\`](@ref)는 왼쪽 나누기 연산자입니다. 정방 행렬의 경우, 결과 `X`는 `A == X*B`를 만족합니다.

또한: [`rdiv!`](@ref).

# 예제

```jldoctest
julia> A = Float64[1 4 5; 3 9 2]; B = Float64[1 4 2; 3 4 2; 8 7 1];

julia> X = A / B
2×3 Matrix{Float64}:
 -0.65   3.75  -1.2
  3.25  -2.75   1.0

julia> isapprox(A, X*B)
true

julia> isapprox(X, A*pinv(B))
true
```
