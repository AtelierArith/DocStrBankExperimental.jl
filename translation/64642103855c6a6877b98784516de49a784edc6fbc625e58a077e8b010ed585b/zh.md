```
checkbounds(Bool, A, I...)
```

如果指定的索引 `I` 在给定数组 `A` 的范围内，则返回 `true`。`AbstractArray` 的子类型应该专门化此方法，如果它们需要提供自定义的边界检查行为；然而，在许多情况下，可以依赖于 `A` 的索引和 [`checkindex`](@ref)。

另请参见 [`checkindex`](@ref)。

# 示例

```jldoctest
julia> A = rand(3, 3);

julia> checkbounds(Bool, A, 2)
true

julia> checkbounds(Bool, A, 3, 4)
false

julia> checkbounds(Bool, A, 1:3)
true

julia> checkbounds(Bool, A, 1:3, 2:4)
false
```
