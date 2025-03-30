```
dropwhile(pred, iter)
```

一个迭代器，它会从 `iter` 中丢弃元素，只要谓词 `pred` 为真，之后返回每个元素。

!!! compat "Julia 1.4"
    此函数至少需要 Julia 1.4。


# 示例

```jldoctest
julia> s = collect(1:5)
5-element Vector{Int64}:
 1
 2
 3
 4
 5

julia> collect(Iterators.dropwhile(<(3),s))
3-element Vector{Int64}:
 3
 4
 5
```
