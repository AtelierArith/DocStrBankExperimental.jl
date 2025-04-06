```
@atomicreplace a.b.x 预期 => 期望
@atomicreplace :sequentially_consistent a.b.x 预期 => 期望
@atomicreplace :sequentially_consistent :monotonic a.b.x 预期 => 期望
```

执行成对的条件替换，原子性地返回值 `(old, success::Bool)`。其中 `success` 表示替换是否完成。

此操作转换为 `replaceproperty!(a.b, :x, 预期, 期望)` 调用。

有关更多详细信息，请参见手册中的 [Per-field atomics](@ref man-atomics) 部分。

# 示例

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomicreplace a.x 1 => 2 # 如果 a 的字段 x 为 1，则用 2 替换，具有顺序一致性
(old = 1, success = true)

julia> @atomic a.x # 以顺序一致性获取 a 的字段 x
2

julia> @atomicreplace a.x 1 => 2 # 如果 a 的字段 x 为 1，则用 2 替换，具有顺序一致性
(old = 2, success = false)

julia> xchg = 2 => 0; # 如果 a 的字段 x 为 2，则用 0 替换，具有顺序一致性

julia> @atomicreplace a.x xchg
(old = 2, success = true)

julia> @atomic a.x # 以顺序一致性获取 a 的字段 x
0
```

!!! compat "Julia 1.7"
    此功能至少需要 Julia 1.7。

