```
conj(A::AbstractArray)
```

배열 `A`의 각 항목에 대한 복소수 켤레를 포함하는 배열을 반환합니다.

`conj.(A)`와 동등하지만, `eltype(A) <: Real`인 경우 `A`는 복사 없이 반환되며, `A`가 0차원일 때는 스칼라 대신 0차원 배열이 반환됩니다.

# 예제

```jldoctest
julia> conj([1, 2im, 3 + 4im])
3-element Vector{Complex{Int64}}:
 1 + 0im
 0 - 2im
 3 - 4im

julia> conj(fill(2 - im))
0-dimensional Array{Complex{Int64}, 0}:
2 + 1im
```
