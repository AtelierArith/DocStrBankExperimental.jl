```
mean(A::AbstractArray; dims)
```

주어진 차원에 대해 배열의 평균을 계산합니다.

!!! compat "Julia 1.1"
    빈 배열에 대한 `mean`은 최소한 Julia 1.1이 필요합니다.


# 예제

```jldoctest
julia> using Statistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> mean(A, dims=1)
1×2 Matrix{Float64}:
 2.0  3.0

julia> mean(A, dims=2)
2×1 Matrix{Float64}:
 1.5
 3.5
```
