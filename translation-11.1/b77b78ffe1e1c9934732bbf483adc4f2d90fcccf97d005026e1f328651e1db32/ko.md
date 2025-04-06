```
maximum(f, A::AbstractArray; dims)
```

주어진 차원에서 배열의 각 요소에 대해 함수 `f`를 호출하여 최대값을 계산합니다.

# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> maximum(abs2, A, dims=1)
1×2 Matrix{Int64}:
 9  16

julia> maximum(abs2, A, dims=2)
2×1 Matrix{Int64}:
  4
 16
```
