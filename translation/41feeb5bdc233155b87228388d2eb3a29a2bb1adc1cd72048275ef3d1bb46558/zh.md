```
Iterators.reverse(itr)
```

给定一个迭代器 `itr`，则 `reverse(itr)` 是一个遍历相同集合但顺序相反的迭代器。这个迭代器是“惰性”的，因为它不会复制集合以进行反转；请参见 [`Base.reverse`](@ref) 以获取急切实现。

（默认情况下，这将返回一个包装 `itr` 的 `Iterators.Reverse` 对象，如果相应的 [`iterate`](@ref) 方法已定义，则该对象是可迭代的，但某些 `itr` 类型可能实现了更专业的 `Iterators.reverse` 行为。）

并非所有迭代器类型 `T` 都支持反向迭代。如果 `T` 不支持，则对 `Iterators.reverse(itr::T)` 进行迭代将抛出 [`MethodError`](@ref)，因为缺少 `Iterators.Reverse{T}` 的 `iterate` 方法。（要实现这些方法，可以通过 `r.itr` 从 `r::Iterators.Reverse{T}` 对象中获取原始迭代器 `itr::T`；更一般地，可以使用 `Iterators.reverse(r)`。）

# 示例

```jldoctest
julia> foreach(println, Iterators.reverse(1:5))
5
4
3
2
1
```
