```
extrema(A::AbstractArray; dims) -> Array{Tuple}
```

주어진 차원에서 배열의 최소 및 최대 요소를 계산합니다.

참고: [`minimum`](@ref), [`maximum`](@ref), [`extrema!`](@ref).

# 예제

```jldoctest
julia> A = reshape(Vector(1:2:16), (2,2,2))
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  5
 3  7

[:, :, 2] =
  9  13
 11  15

julia> extrema(A, dims = (1,2))
1×1×2 Array{Tuple{Int64, Int64}, 3}:
[:, :, 1] =
 (1, 7)

[:, :, 2] =
 (9, 15)
```
