```
inv(M)
```

행렬의 역행렬. 행렬 `M`에 대해 `M * N = I`가 성립하는 행렬 `N`을 계산합니다. 여기서 `I`는 단위 행렬입니다. 왼쪽 나눗셈 `N = M \ I`를 풀어서 계산됩니다.

# 예제

```jldoctest
julia> M = [2 5; 1 3]
2×2 Matrix{Int64}:
 2  5
 1  3

julia> N = inv(M)
2×2 Matrix{Float64}:
  3.0  -5.0
 -1.0   2.0

julia> M*N == N*M == Matrix(I, 2, 2)
true
```
