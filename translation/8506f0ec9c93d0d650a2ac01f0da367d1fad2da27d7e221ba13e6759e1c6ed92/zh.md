```
@atomicswap a.b.x = new
@atomicswap :sequentially_consistent a.b.x = new
```

将 `new` 存储到 `a.b.x` 中，并返回 `a.b.x` 的旧值。

此操作转换为 `swapproperty!(a.b, :x, new)` 调用。

有关更多详细信息，请参见手册中的 [Per-field atomics](@ref man-atomics) 部分。

# 示例

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomicswap a.x = 2+2 # 用 4 替换 a 的字段 x，具有顺序一致性
1

julia> @atomic a.x # 获取 a 的字段 x，具有顺序一致性
4
```

!!! compat "Julia 1.7"
    此功能至少需要 Julia 1.7。

