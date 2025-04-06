```
NTuple{N, T}
```

一种紧凑的方式来表示长度为 `N` 的元组类型，其中所有元素都是类型 `T`。

# 示例

```jldoctest
julia> isa((1, 2, 3, 4, 5, 6), NTuple{6, Int})
true
```

另见 [`ntuple`](@ref).
