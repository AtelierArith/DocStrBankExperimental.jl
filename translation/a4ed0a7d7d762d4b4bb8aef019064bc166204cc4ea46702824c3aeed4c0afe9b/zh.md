```
@atomiconce a.b.x = value
@atomiconce :sequentially_consistent a.b.x = value
@atomiconce :sequentially_consistent :monotonic a.b.x = value
```

如果之前未设置，则以原子方式执行值的条件赋值，返回值 `success::Bool`。其中 `success` 表示赋值是否完成。

此操作转换为 `setpropertyonce!(a.b, :x, value)` 调用。

有关更多详细信息，请参见手册中的 [Per-field atomics](@ref man-atomics) 部分。

# 示例

```jldoctest
julia> mutable struct AtomicOnce
           @atomic x
           AtomicOnce() = new()
       end

julia> a = AtomicOnce()
AtomicOnce(#undef)

julia> @atomiconce a.x = 1 # 如果未设置，则以顺序一致性将 a 的字段 x 设置为 1
true

julia> @atomic a.x # 以顺序一致性获取 a 的字段 x
1

julia> @atomiconce a.x = 1 # 如果未设置，则以顺序一致性将 a 的字段 x 设置为 1
false
```

!!! compat "Julia 1.11"
    此功能至少需要 Julia 1.11。

