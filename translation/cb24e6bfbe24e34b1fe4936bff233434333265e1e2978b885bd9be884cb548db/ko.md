```
Array{T}(nothing, dims)
Array{T,N}(nothing, dims)
```

`T` 유형의 요소를 포함하는 `N`-차원 [`Array`](@ref)를 생성하며, [`nothing`](@ref) 항목으로 초기화됩니다. 요소 유형 `T`는 이러한 값을 수용할 수 있어야 하며, 즉 `Nothing <: T` 여야 합니다.

# 예제

```jldoctest
julia> Array{Union{Nothing, String}}(nothing, 2)
2-element Vector{Union{Nothing, String}}:
 nothing
 nothing

julia> Array{Union{Nothing, Int}}(nothing, 2, 3)
2×3 Matrix{Union{Nothing, Int64}}:
 nothing  nothing  nothing
 nothing  nothing  nothing
```
