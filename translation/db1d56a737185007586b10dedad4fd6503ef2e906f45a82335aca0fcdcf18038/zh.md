```
dot(x, y)
x ⋅ y
```

计算两个向量之间的点积。对于复向量，第一个向量是共轭的。

`dot` 也适用于任意可迭代对象，包括任何维度的数组，只要在元素上定义了 `dot`。

`dot` 在语义上等价于 `sum(dot(vx,vy) for (vx,vy) in zip(x, y))`，但增加了参数必须具有相等长度的限制。

`x ⋅ y`（其中 `⋅` 可以通过在 REPL 中输入 `\cdot` 后按 Tab 键来输入）是 `dot(x, y)` 的同义词。

# 示例

```jldoctest
julia> dot([1; 1], [2; 3])
5

julia> dot([im; im], [1; 1])
0 - 2im

julia> dot(1:5, 2:6)
70

julia> x = fill(2., (5,5));

julia> y = fill(3., (5,5));

julia> dot(x, y)
150.0
```
