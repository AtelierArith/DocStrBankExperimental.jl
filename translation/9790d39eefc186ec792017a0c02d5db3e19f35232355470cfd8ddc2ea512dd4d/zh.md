```
drop(iter, n)
```

一个生成 `iter` 中除前 `n` 个元素外所有元素的迭代器。

# 示例

```jldoctest
julia> a = 1:2:11
1:2:11

julia> collect(a)
6-element Vector{Int64}:
  1
  3
  5
  7
  9
 11

julia> collect(Iterators.drop(a,4))
2-element Vector{Int64}:
  9
 11
```
