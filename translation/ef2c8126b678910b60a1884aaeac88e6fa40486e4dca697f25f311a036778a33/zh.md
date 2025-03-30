```
Matrix{T}(missing, m, n)
```

构造一个 [`Matrix{T}`](@ref)，大小为 `m`×`n`，初始化为 [`missing`](@ref) 条目。元素类型 `T` 必须能够容纳这些值，即 `Missing <: T`。

# 示例

```jldoctest
julia> Matrix{Union{Missing, String}}(missing, 2, 3)
2×3 Matrix{Union{Missing, String}}:
 missing  missing  missing
 missing  missing  missing
```
