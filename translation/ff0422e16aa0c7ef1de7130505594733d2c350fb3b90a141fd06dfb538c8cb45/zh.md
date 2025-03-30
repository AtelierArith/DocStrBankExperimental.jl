```
isdisjoint(a, b) -> Bool
```

确定集合 `a` 和 `b` 是否不相交。等价于 `isempty(a ∩ b)`，但在可能的情况下更高效。

另请参见: [`intersect`](@ref), [`isempty`](@ref), [`issetequal`](@ref)。

!!! compat "Julia 1.5"
    此函数至少需要 Julia 1.5。


# 示例

```jldoctest
julia> isdisjoint([1, 2], [2, 3, 4])
false

julia> isdisjoint([3, 1], [2, 4])
true
```
