```
count([f=identity,] A::AbstractArray; dims=:)
```

주어진 차원에 대해 `f`가 `true`를 반환하는 `A`의 요소 수를 계산합니다.

!!! compat "Julia 1.5"
    `dims` 키워드는 Julia 1.5에서 추가되었습니다.


!!! compat "Julia 1.6"
    `init` 키워드는 Julia 1.6에서 추가되었습니다.


# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> count(<=(2), A, dims=1)
1×2 Matrix{Int64}:
 1  1

julia> count(<=(2), A, dims=2)
2×1 Matrix{Int64}:
 2
 0
```
