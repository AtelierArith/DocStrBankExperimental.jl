```
to_indices(A, I::Tuple)
```

将元组 `I` 转换为用于索引数组 `A` 的索引元组。

返回的元组必须仅包含 `Int` 或 `AbstractArray` 的标量索引，这些索引是数组 `A` 所支持的。遇到未知的索引类型时将会报错。

对于简单的索引类型，它会调用未导出的 `Base.to_index(A, i)` 来处理每个索引 `i`。虽然这个内部函数并不打算直接调用，但 `Base.to_index` 可以通过自定义数组或索引类型进行扩展，以提供自定义的索引行为。

更复杂的索引类型可能需要更多关于它们索引的维度的上下文。为了支持这些情况，`to_indices(A, I)` 调用 `to_indices(A, axes(A), I)`，然后递归地遍历给定的索引元组和 `A` 的维度索引。因此，并不是所有的索引类型都能保证传播到 `Base.to_index`。

# 示例

```jldoctest
julia> A = zeros(1,2,3,4);

julia> to_indices(A, (1,1,2,2))
(1, 1, 2, 2)

julia> to_indices(A, (1,1,2,20)) # 不进行边界检查
(1, 1, 2, 20)

julia> to_indices(A, (CartesianIndex((1,)), 2, CartesianIndex((3,4)))) # 异常索引
(1, 2, 3, 4)

julia> to_indices(A, ([1,1], 1:2, 3, 4))
([1, 1], 1:2, 3, 4)

julia> to_indices(A, (1,2)) # 不进行形状检查
(1, 2)
```
