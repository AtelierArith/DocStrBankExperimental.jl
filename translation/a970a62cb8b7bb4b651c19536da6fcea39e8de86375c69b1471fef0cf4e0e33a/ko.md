```
sum(f, A::AbstractArray; dims)
```

주어진 차원에 대해 배열의 각 요소에 함수 `f`를 호출한 결과를 합산합니다.

# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> sum(abs2, A, dims=1)
1×2 Matrix{Int64}:
 10  20

julia> sum(abs2, A, dims=2)
2×1 Matrix{Int64}:
  5
 25
```
