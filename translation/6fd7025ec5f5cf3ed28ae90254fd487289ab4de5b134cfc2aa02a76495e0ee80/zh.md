```
foreach(f, c...) -> Nothing
```

在可迭代对象 `c` 的每个元素上调用函数 `f`。对于多个可迭代参数，`f` 按元素调用，当任何迭代器完成时，迭代停止。

当不需要 `f` 的结果时，应使用 `foreach` 而不是 [`map`](@ref)，例如在 `foreach(println, array)` 中。

# 示例

```jldoctest
julia> tri = 1:3:7; res = Int[];

julia> foreach(x -> push!(res, x^2), tri)

julia> res
3-element Vector{Int64}:
  1
 16
 49

julia> foreach((x, y) -> println(x, " with ", y), tri, 'a':'z')
1 with a
4 with b
7 with c
```
