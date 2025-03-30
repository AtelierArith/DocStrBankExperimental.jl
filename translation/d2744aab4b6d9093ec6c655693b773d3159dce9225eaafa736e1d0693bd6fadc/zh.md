```
keepat!(a::Vector, inds)
keepat!(a::BitVector, inds)
```

移除所有未在 `inds` 中给出的索引处的项，并返回修改后的 `a`。保留的项会被移动以填补结果中的空缺。

!!! 警告     当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。

`inds` 必须是一个排序且唯一的整数索引的迭代器。另见 [`deleteat!`](@ref)。

!!! 兼容 "Julia 1.7"     此函数自 Julia 1.7 起可用。

# 示例

```jldoctest
julia> keepat!([6, 5, 4, 3, 2, 1], 1:2:5)
3-element Vector{Int64}:
 6
 4
 2
```
