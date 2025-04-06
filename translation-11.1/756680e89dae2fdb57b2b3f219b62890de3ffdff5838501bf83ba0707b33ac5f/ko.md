```
ndims(A::AbstractArray) -> Integer
```

`A`의 차원 수를 반환합니다.

참고: [`size`](@ref), [`axes`](@ref).

# 예제

```jldoctest
julia> A = fill(1, (3,4,5));

julia> ndims(A)
3
```
