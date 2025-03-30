```
Vector{T}(nothing, m)
```

构造一个 [`Vector{T}`](@ref)，长度为 `m`，初始化为 [`nothing`](@ref) 条目。元素类型 `T` 必须能够容纳这些值，即 `Nothing <: T`。

# 示例

```jldoctest
julia> Vector{Union{Nothing, String}}(nothing, 2)
2-element Vector{Union{Nothing, String}}:
 nothing
 nothing
```
