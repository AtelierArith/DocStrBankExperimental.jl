```
Array{T}(missing, dims)
Array{T,N}(missing, dims)
```

构造一个 `N` 维的 [`Array`](@ref)，包含类型为 `T` 的元素，初始化为 [`missing`](@ref) 条目。元素类型 `T` 必须能够容纳这些值，即 `Missing <: T`。

# 示例

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
