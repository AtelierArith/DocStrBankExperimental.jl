```
isless(x, y)
```

测试 `x` 是否小于 `y`，根据固定的全序（与 [`isequal`](@ref) 一起定义）。`isless` 并未为所有类型的对 `(x, y)` 定义。然而，如果它被定义，则期望满足以下条件：

  * 如果 `isless(x, y)` 被定义，则 `isless(y, x)` 和 `isequal(x, y)` 也被定义，并且这三者中恰好有一个返回 `true`。
  * `isless` 定义的关系是传递的，即 `isless(x, y) && isless(y, z)` 意味着 `isless(x, z)`。

通常无序的值，如 `NaN`，在常规值之后排序。 [`missing`](@ref) 值排在最后。

这是 [`sort!`](@ref) 使用的默认比较。

# 实现

具有全序的非数值类型应实现此函数。数值类型仅在具有特殊值（如 `NaN`）时需要实现它。具有部分序的类型应实现 [`<`](@ref)。有关如何定义可用于排序和相关函数的替代排序方法，请参见 [Alternate Orderings](@ref) 的文档。

# 示例

```jldoctest
julia> isless(1, 3)
true

julia> isless("Red", "Blue")
false
```
