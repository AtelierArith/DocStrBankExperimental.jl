```
@atomic var
@atomic order ex
```

将 `var` 或 `ex` 标记为以原子方式执行，如果 `ex` 是一个支持的表达式。如果未指定 `order`，则默认为 :sequentially_consistent。

```
@atomic a.b.x = new
@atomic a.b.x += addend
@atomic :release a.b.x = new
@atomic :acquire_release a.b.x += addend
```

以原子方式执行右侧表达的存储操作并返回新值。

使用 `=` 时，此操作转换为 `setproperty!(a.b, :x, new)` 调用。使用任何运算符时，此操作也转换为 `modifyproperty!(a.b, :x, +, addend)[2]` 调用。

```
@atomic a.b.x max arg2
@atomic a.b.x + arg2
@atomic max(a.b.x, arg2)
@atomic :acquire_release max(a.b.x, arg2)
@atomic :acquire_release a.b.x + arg2
@atomic :acquire_release a.b.x max arg2
```

以原子方式执行右侧表达的二元操作。将结果存储到第一个参数中的字段，并返回值 `(old, new)`。

此操作转换为 `modifyproperty!(a.b, :x, func, arg2)` 调用。

有关更多详细信息，请参见手册中的 [Per-field atomics](@ref man-atomics) 部分。

# 示例

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomic a.x # 以顺序一致性获取 a 的字段 x
1

julia> @atomic :sequentially_consistent a.x = 2 # 以顺序一致性设置 a 的字段 x
2

julia> @atomic a.x += 1 # 以顺序一致性递增 a 的字段 x
3

julia> @atomic a.x + 1 # 以顺序一致性递增 a 的字段 x
3 => 4

julia> @atomic a.x # 以顺序一致性获取 a 的字段 x
4

julia> @atomic max(a.x, 10) # 以顺序一致性将 a 的字段 x 更改为最大值
4 => 10

julia> @atomic a.x max 5 # 再次以顺序一致性将 a 的字段 x 更改为最大值
10 => 10
```

!!! compat "Julia 1.7"
    此功能需要至少 Julia 1.7。

