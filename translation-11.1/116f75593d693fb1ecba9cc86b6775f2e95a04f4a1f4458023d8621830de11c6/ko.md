```
Array{T}(missing, dims)
Array{T,N}(missing, dims)
```

`T` 유형의 요소를 포함하는 `N`-차원 [`Array`](@ref)를 생성하며, [`missing`](@ref) 항목으로 초기화됩니다. 요소 유형 `T`는 이러한 값을 수용할 수 있어야 하며, 즉 `Missing <: T` 여야 합니다.

# 예제

```jldoctest
julia> Array{Union{Missing, String}}(missing, 2)
2-element Vector{Union{Missing, String}}:
 missing
 missing

julia> Array{Union{Missing, Int}}(missing, 2, 3)
2×3 Matrix{Union{Missing, Int64}}:
 missing  missing  missing
 missing  missing  missing
```
