```
mapreduce(f, op, itrs...; [init])
```

将函数 `f` 应用到 `itrs` 中的每个元素，然后使用二元函数 `op` 来减少结果。如果提供，`init` 必须是 `op` 的中性元素，将在空集合中返回。对于非空集合是否使用 `init` 是未指定的。一般来说，处理空集合时需要提供 `init`。

[`mapreduce`](@ref) 在功能上等同于调用 `reduce(op, map(f, itr); init=init)`，但通常执行速度更快，因为不需要创建中间集合。有关 [`reduce`](@ref) 和 [`map`](@ref) 的文档，请参见。

!!! compat "Julia 1.2"
    `mapreduce` 需要 Julia 1.2 或更高版本才能与多个迭代器一起使用。


# 示例

```jldoctest
julia> mapreduce(x->x^2, +, [1:3;]) # == 1 + 4 + 9
14
```

归约的结合性依赖于实现。此外，一些实现可能会重用 `f` 的返回值，对于在 `itr` 中多次出现的元素。要保证左或右结合性并对每个值调用 `f`，请使用 [`mapfoldl`](@ref) 或 [`mapfoldr`](@ref)。
