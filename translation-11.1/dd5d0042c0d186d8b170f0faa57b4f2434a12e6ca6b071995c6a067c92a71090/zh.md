```
Vector{T}(missing, m)
```

构造一个 [`Vector{T}`](@ref)，长度为 `m`，初始化为 [`missing`](@ref) 条目。元素类型 `T` 必须能够容纳这些值，即 `Missing <: T`。

# 示例

```jldoctest
julia> Vector{Union{Missing, String}}(missing, 2)
2-element Vector{Union{Missing, String}}:
 missing
 missing
```
