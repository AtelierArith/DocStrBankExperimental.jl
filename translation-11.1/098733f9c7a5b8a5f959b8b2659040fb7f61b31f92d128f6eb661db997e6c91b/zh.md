```
checkindex(Bool, inds::AbstractUnitRange, index)
```

如果给定的 `index` 在 `inds` 的范围内，则返回 `true`。希望作为所有数组的索引行为的自定义类型可以扩展此方法，以提供专门的边界检查实现。

另见 [`checkbounds`](@ref)。

# 示例

```jldoctest
julia> checkindex(Bool, 1:20, 8)
true

julia> checkindex(Bool, 1:20, 21)
false
```
