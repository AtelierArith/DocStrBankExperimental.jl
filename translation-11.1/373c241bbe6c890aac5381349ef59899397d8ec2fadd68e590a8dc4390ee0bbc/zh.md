```
Matrix{T}(nothing, m, n)
```

构造一个 [`Matrix{T}`](@ref)，大小为 `m`×`n`，初始化为 [`nothing`](@ref) 条目。元素类型 `T` 必须能够容纳这些值，即 `Nothing <: T`。

# 示例

```jldoctest
julia> Matrix{Union{Nothing, String}}(nothing, 2, 3)
2×3 Matrix{Union{Nothing, String}}:
 nothing  nothing  nothing
 nothing  nothing  nothing
```
