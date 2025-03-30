```
IteratorSize(itertype::Type) -> IteratorSize
```

给定迭代器的类型，返回以下值之一：

  * `SizeUnknown()` 如果长度（元素数量）无法提前确定。
  * `HasLength()` 如果有固定的有限长度。
  * `HasShape{N}()` 如果有已知的长度加上多维形状的概念（如数组）。在这种情况下，`N` 应该给出维度的数量，并且 [`axes`](@ref) 函数对迭代器是有效的。
  * `IsInfinite()` 如果迭代器永远产生值。

默认值（对于未定义此函数的迭代器）是 `HasLength()`。这意味着大多数迭代器被假定实现了 [`length`](@ref)。

此特性通常用于在预分配结果空间的算法和逐步调整结果大小的算法之间进行选择。

```jldoctest
julia> Base.IteratorSize(1:5)
Base.HasShape{1}()

julia> Base.IteratorSize((2,3))
Base.HasLength()
```
