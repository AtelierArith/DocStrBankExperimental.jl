```
symdiff(s, itrs...)
```

构造传入集合中元素的对称差。当 `s` 不是 `AbstractSet` 时，顺序保持不变。

另见 [`symdiff!`](@ref), [`setdiff`](@ref), [`union`](@ref) 和 [`intersect`](@ref)。

# 示例

```jldoctest
julia> symdiff([1,2,3], [3,4,5], [4,5,6])
3-element Vector{Int64}:
 1
 2
 6

julia> symdiff([1,2,1], [2, 1, 2])
Int64[]
```
