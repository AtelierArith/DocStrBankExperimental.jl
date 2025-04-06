```
rest(iter, state)
```

一个迭代器，它产生与 `iter` 相同的元素，但从给定的 `state` 开始。

另请参见: [`Iterators.drop`](@ref), [`Iterators.peel`](@ref), [`Base.rest`](@ref).

# 示例

```jldoctest
julia> collect(Iterators.rest([1,2,3,4], 2))
3-element Vector{Int64}:
 2
 3
 4
```
