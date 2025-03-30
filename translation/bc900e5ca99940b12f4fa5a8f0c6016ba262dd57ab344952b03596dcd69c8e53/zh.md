```
IteratorEltype(itertype::Type) -> IteratorEltype
```

给定一个迭代器的类型，返回以下值之一：

  * `EltypeUnknown()` 如果迭代器所产生的元素类型事先未知。
  * `HasEltype()` 如果元素类型已知，并且 [`eltype`](@ref) 将返回一个有意义的值。

`HasEltype()` 是默认值，因为假设迭代器实现了 [`eltype`](@ref)。

这个特性通常用于在预分配特定类型结果的算法和根据产生值的类型选择结果类型的算法之间进行选择。

```jldoctest
julia> Base.IteratorEltype(1:5)
Base.HasEltype()
```
