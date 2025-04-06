```
replace(A, old_new::Pair...; [count::Integer])
```

返回集合 `A` 的副本，其中，对于每对 `old=>new` 在 `old_new` 中，所有 `old` 的出现都被替换为 `new`。相等性使用 [`isequal`](@ref) 确定。如果指定了 `count`，则最多替换 `count` 次出现。

结果的元素类型是基于 `A` 的元素类型和对中的 `new` 值的类型使用提升（参见 [`promote_type`](@ref)）来选择。如果省略 `count` 并且 `A` 的元素类型是 `Union`，则结果的元素类型将不包括被替换为不同类型值的单例类型：例如，如果 `missing` 被替换，`Union{T,Missing}` 将变为 `T`。

另请参见 [`replace!`](@ref), [`splice!`](@ref), [`delete!`](@ref), [`insert!`](@ref).

!!! compat "Julia 1.7"
    需要版本 1.7 来替换 `Tuple` 的元素。


# 示例

```jldoctest
julia> replace([1, 2, 1, 3], 1=>0, 2=>4, count=2)
4-element Vector{Int64}:
 0
 4
 1
 3

julia> replace([1, missing], missing=>0)
2-element Vector{Int64}:
 1
 0
```
