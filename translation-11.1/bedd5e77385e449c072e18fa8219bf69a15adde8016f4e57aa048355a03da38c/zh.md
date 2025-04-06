```
product(iters...)
```

返回一个迭代器，该迭代器生成多个迭代器的乘积。每个生成的元素都是一个元组，其第 `i` 个元素来自第 `i` 个参数迭代器。第一个迭代器变化最快。

另请参见: [`zip`](@ref), [`Iterators.flatten`](@ref).

# 示例

```jldoctest
julia> collect(Iterators.product(1:2, 3:5))
2×3 Matrix{Tuple{Int64, Int64}}:
 (1, 3)  (1, 4)  (1, 5)
 (2, 3)  (2, 4)  (2, 5)

julia> ans == [(x,y) for x in 1:2, y in 3:5]  # 收集一个涉及 Iterators.product 的生成器
true
```
