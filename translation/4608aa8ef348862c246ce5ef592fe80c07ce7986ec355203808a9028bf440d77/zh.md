```
isempty(collection) -> Bool
```

确定一个集合是否为空（没有元素）。

!!! warning
    `isempty(itr)` 可能会消耗状态迭代器 `itr` 的下一个元素，除非定义了适当的 [`Base.isdone(itr)`](@ref) 方法。状态迭代器 *应该* 实现 `isdone`，但在编写应该支持任何迭代器类型的通用代码时，您可能想要避免使用 `isempty`。


# 示例

```jldoctest
julia> isempty([])
true

julia> isempty([1 2 3])
false
```
