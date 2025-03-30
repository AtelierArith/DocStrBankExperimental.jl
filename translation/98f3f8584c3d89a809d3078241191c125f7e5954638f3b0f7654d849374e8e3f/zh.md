```
partialsortperm(v, k; by=identity, lt=isless, rev=false)
```

返回向量 `v` 的部分排列 `I`，使得 `v[I]` 在索引 `k` 处返回 `v` 的完全排序版本的值。如果 `k` 是一个范围，则返回一个索引向量；如果 `k` 是一个整数，则返回一个单一索引。顺序使用与 `sort!` 相同的关键字指定。该排列是稳定的：相等元素的索引将按升序出现。

此函数等效于但比调用 `sortperm(...)[k]` 更高效。

# 示例

```jldoctest
julia> v = [3, 1, 2, 1];

julia> v[partialsortperm(v, 1)]
1

julia> p = partialsortperm(v, 1:3)
3-element view(::Vector{Int64}, 1:3) with eltype Int64:
 2
 4
 3

julia> v[p]
3-element Vector{Int64}:
 1
 1
 2
```
