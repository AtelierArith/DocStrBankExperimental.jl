```
flatten(iter)
```

给定一个返回迭代器的迭代器，返回一个返回这些迭代器元素的迭代器。换句话说，参数迭代器的元素被连接在一起。

# 示例

```jldoctest
julia> collect(Iterators.flatten((1:2, 8:9)))
4-element Vector{Int64}:
 1
 2
 8
 9

julia> [(x,y) for x in 0:1 for y in 'a':'c']  # 收集涉及 Iterators.flatten 的生成器
6-element Vector{Tuple{Int64, Char}}:
 (0, 'a')
 (0, 'b')
 (0, 'c')
 (1, 'a')
 (1, 'b')
 (1, 'c')
```
