```
pop!(collection) -> item
```

`collection`에서 항목을 제거하고 반환합니다. `collection`이 정렬된 컨테이너인 경우 마지막 항목이 반환되며, 비정렬 컨테이너의 경우 임의의 요소가 반환됩니다.

참고: [`popfirst!`](@ref), [`popat!`](@ref), [`delete!`](@ref), [`deleteat!`](@ref), [`splice!`](@ref), 및 [`push!`](@ref).

# 예제

```jldoctest
julia> A=[1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> pop!(A)
3

julia> A
2-element Vector{Int64}:
 1
 2

julia> S = Set([1, 2])
Set{Int64} with 2 elements:
  2
  1

julia> pop!(S)
2

julia> S
Set{Int64} with 1 element:
  1

julia> pop!(Dict(1=>2))
1 => 2
```
