```
Bidiagonal(A, uplo::Symbol)
```

주어진 행렬 `A`의 주 대각선과 첫 번째 초대각선(만약 `uplo=:U`인 경우) 또는 첫 번째 아랫대각선(만약 `uplo=:L`인 경우)으로부터 `Bidiagonal` 행렬을 생성합니다.

# 예제

```jldoctest
julia> A = [1 1 1 1; 2 2 2 2; 3 3 3 3; 4 4 4 4]
4×4 Matrix{Int64}:
 1  1  1  1
 2  2  2  2
 3  3  3  3
 4  4  4  4

julia> Bidiagonal(A, :U) # A의 주 대각선과 첫 번째 초대각선을 포함
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  1  ⋅  ⋅
 ⋅  2  2  ⋅
 ⋅  ⋅  3  3
 ⋅  ⋅  ⋅  4

julia> Bidiagonal(A, :L) # A의 주 대각선과 첫 번째 아랫대각선을 포함
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  ⋅  ⋅  ⋅
 2  2  ⋅  ⋅
 ⋅  3  3  ⋅
 ⋅  ⋅  4  4
```
