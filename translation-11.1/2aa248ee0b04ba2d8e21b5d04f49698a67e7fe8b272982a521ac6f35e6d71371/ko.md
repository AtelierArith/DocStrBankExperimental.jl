```
real(A::AbstractArray)
```

배열 `A`의 각 항목의 실수 부분을 포함하는 배열을 반환합니다.

`real.(A)`와 동등하지만, `eltype(A) <: Real`인 경우 `A`는 복사 없이 반환되며, `A`가 0차원일 때는 스칼라 대신 0차원 배열이 반환됩니다.

# 예제

```jldoctest
julia> real([1, 2im, 3 + 4im])
3-element Vector{Int64}:
 1
 0
 3

julia> real(fill(2 - im))
0-dimensional Array{Int64, 0}:
2
```
