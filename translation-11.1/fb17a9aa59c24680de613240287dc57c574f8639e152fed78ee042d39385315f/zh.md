```
∉(item, collection) -> Bool
∌(collection, item) -> Bool
```

`∈` 和 `∋` 的否定，即检查 `item` 是否不在 `collection` 中。

当使用 `items .∉ collection` 进行广播时，`item` 和 `collection` 都会被广播，这通常不是预期的结果。例如，如果两个参数都是向量（并且维度匹配），结果是一个向量，指示 `collection` 中的每个值在 `collection` 中对应位置的值是否不在 `items` 中。要获取一个指示 `items` 中每个值是否不在 `collection` 中的向量，可以将 `collection` 包装在一个元组或 `Ref` 中，如下所示：`items .∉ Ref(collection)`。

# 示例

```jldoctest
julia> 1 ∉ 2:4
true

julia> 1 ∉ 1:3
false

julia> [1, 2] .∉ [2, 3]
2-element BitVector:
 1
 1

julia> [1, 2] .∉ ([2, 3],)
2-element BitVector:
 1
 0
```
