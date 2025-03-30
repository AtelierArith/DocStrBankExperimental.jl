```
prod(f, A::AbstractArray; dims)
```

주어진 차원에 대해 배열의 각 요소에 대한 함수 `f` 호출 결과를 곱합니다.

# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> prod(abs2, A, dims=1)
1×2 Matrix{Int64}:
 9  64

julia> prod(abs2, A, dims=2)
2×1 Matrix{Int64}:
   4
 144
```
