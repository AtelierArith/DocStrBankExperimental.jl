```
Diagonal(A::AbstractMatrix)
```

행렬 `A`의 주 대각선으로부터 행렬을 구성합니다. 입력 행렬 `A`는 직사각형일 수 있지만, 출력은 정사각형이 됩니다.

# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> D = Diagonal(A)
2×2 Diagonal{Int64, Vector{Int64}}:
 1  ⋅
 ⋅  4

julia> A = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> Diagonal(A)
2×2 Diagonal{Int64, Vector{Int64}}:
 1  ⋅
 ⋅  5
```
