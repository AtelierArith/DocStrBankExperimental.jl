```
Tridiagonal(A)
```

행렬 `A`의 첫 번째 하삼각 대각선, 대각선 및 첫 번째 상삼각 대각선으로부터 삼대각 행렬을 구성합니다.

# 예제

```jldoctest
julia> A = [1 2 3 4; 1 2 3 4; 1 2 3 4; 1 2 3 4]
4×4 Matrix{Int64}:
 1  2  3  4
 1  2  3  4
 1  2  3  4
 1  2  3  4

julia> Tridiagonal(A)
4×4 Tridiagonal{Int64, Vector{Int64}}:
 1  2  ⋅  ⋅
 1  2  3  ⋅
 ⋅  2  3  4
 ⋅  ⋅  3  4
```
