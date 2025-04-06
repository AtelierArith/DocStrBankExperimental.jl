```
reverse(A; dims=:)
```

`dims`에 따라 `A`를 반전시킵니다. `dims`는 정수(단일 차원), 정수의 튜플(차원의 튜플) 또는 `:`(모든 차원에서 반전, 기본값)일 수 있습니다. 제자리 반전을 위해 [`reverse!`](@ref)도 참조하십시오.

# 예제

```jldoctest
julia> b = Int64[1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> reverse(b, dims=2)
2×2 Matrix{Int64}:
 2  1
 4  3

julia> reverse(b)
2×2 Matrix{Int64}:
 4  3
 2  1
```

!!! compat "Julia 1.6"
    Julia 1.6 이전에는 `reverse`에서 단일 정수 `dims`만 지원됩니다.

