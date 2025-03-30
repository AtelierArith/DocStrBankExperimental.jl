```
Array{T}(nothing, dims)
Array{T,N}(nothing, dims)
```

构造一个 `N` 维的 [`Array`](@ref)，包含类型为 `T` 的元素，初始化为 [`nothing`](@ref) 条目。元素类型 `T` 必须能够容纳这些值，即 `Nothing <: T`。

# 示例

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
