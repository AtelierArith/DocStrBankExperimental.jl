```
Broadcast.broadcastable(x)
```

返回 `x` 或一个类似 `x` 的对象，使其支持 [`axes`](@ref)、索引，并且其类型支持 [`ndims`](@ref)。

如果 `x` 支持迭代，则返回的值应具有与 [`collect(x)`](@ref) 相同的 `axes` 和索引行为。

如果 `x` 不是 `AbstractArray` 但支持 `axes`、索引，并且其类型支持 `ndims`，那么 `broadcastable(::typeof(x))` 可以实现为仅返回自身。此外，如果 `x` 定义了自己的 [`BroadcastStyle`](@ref)，那么它必须定义其 `broadcastable` 方法以返回自身，以便自定义样式生效。

# 示例

```jldoctest
julia> Broadcast.broadcastable([1,2,3]) # 像 `identity`，因为数组已经支持 axes 和索引
3-element Vector{Int64}:
 1
 2
 3

julia> Broadcast.broadcastable(Int) # 类型不支持 axes、索引或迭代，但通常用作标量
Base.RefValue{Type{Int64}}(Int64)

julia> Broadcast.broadcastable("hello") # 字符串打破了匹配迭代的惯例，表现得像标量
Base.RefValue{String}("hello")
```
