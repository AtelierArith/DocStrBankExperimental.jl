```
takewhile(pred, iter)
```

一个迭代器，它从 `iter` 中生成元素，只要谓词 `pred` 为真，之后将丢弃每个元素。

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

julia> collect(Iterators.takewhile(<(3),s))
2-element Vector{Int64}:
 1
 2
```
