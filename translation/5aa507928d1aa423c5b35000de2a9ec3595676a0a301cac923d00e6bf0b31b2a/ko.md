```
median(A::AbstractArray; dims)
```

주어진 차원에 따라 배열의 중앙값을 계산합니다.

# 예제

```jldoctest
julia> using Statistics

julia> median([1 2; 3 4], dims=1)
1×2 Matrix{Float64}:
 2.0  3.0
```
