```
in(item, collection) -> Bool
∈(item, collection) -> Bool
```

确定一个项目是否在给定的集合中，意思是它与通过迭代集合生成的一个值 [`==`](@ref) 相等。返回一个 `Bool` 值，除非 `item` 是 [`missing`](@ref) 或 `collection` 包含 `missing` 但不包含 `item`，在这种情况下返回 `missing`（[三值逻辑](https://en.wikipedia.org/wiki/Three-valued_logic)，与 [`any`](@ref) 和 [`==`](@ref) 的行为相匹配）。

一些集合遵循稍微不同的定义。例如，[`Set`](@ref)s 检查项目是否 [`isequal`](@ref) 于其中一个元素；[`Dict`](@ref)s 查找 `key=>value` 对，并且 `key` 使用 [`isequal`](@ref) 进行比较。

要测试字典中是否存在键，请使用 [`haskey`](@ref) 或 `k in keys(dict)`。对于上述提到的集合，结果始终是一个 `Bool`。

当使用 `in.(items, collection)` 或 `items .∈ collection` 进行广播时，`item` 和 `collection` 都会被广播，这通常不是预期的结果。例如，如果两个参数都是向量（并且维度匹配），结果是一个向量，指示集合 `items` 中的每个值是否在 `collection` 中对应位置的值中。要获取一个指示 `items` 中每个值是否在 `collection` 中的向量，可以将 `collection` 包装在一个元组或 `Ref` 中，如下所示：`in.(items, Ref(collection))` 或 `items .∈ Ref(collection)`。

另请参见：[`∉`](@ref)，[`insorted`](@ref)，[`contains`](@ref)，[`occursin`](@ref)，[`issubset`](@ref)。

# 示例

```jldoctest
julia> a = 1:3:20
1:3:19

julia> 4 in a
true

julia> 5 in a
false

julia> missing in [1, 2]
missing

julia> 1 in [2, missing]
missing

julia> 1 in [1, missing]
true

julia> missing in Set([1, 2])
false

julia> (1=>missing) in Dict(1=>10, 2=>20)
missing

julia> [1, 2] .∈ [2, 3]
2-element BitVector:
 0
 0

julia> [1, 2] .∈ ([2, 3],)
2-element BitVector:
 0
 1
```
