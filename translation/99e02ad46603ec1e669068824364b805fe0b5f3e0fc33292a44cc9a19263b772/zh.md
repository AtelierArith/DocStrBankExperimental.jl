```
issetequal(a, b) -> Bool
```

确定 `a` 和 `b` 是否具有相同的元素。等价于 `a ⊆ b && b ⊆ a`，但在可能的情况下更高效。

另请参见: [`isdisjoint`](@ref), [`union`](@ref)。

# 示例

```jldoctest
julia> issetequal([1, 2], [1, 2, 3])
false

julia> issetequal([1, 2], [2, 1])
true
```
