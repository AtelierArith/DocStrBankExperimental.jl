```
dot(x, A, y)
```

计算两个向量 `x` 和 `y` 之间的广义点积 `dot(x, A*y)`，而不存储中间结果 `A*y`。与两个参数的 [`dot(_,_)`](@ref) 一样，这个操作是递归的。此外，对于复数向量，第一个向量会被共轭。

!!! compat "Julia 1.4"
    三个参数的 `dot` 至少需要 Julia 1.4。


# 示例

```jldoctest
julia> dot([1; 1], [1 2; 3 4], [2; 3])
26

julia> dot(1:5, reshape(1:25, 5, 5), 2:6)
4850

julia> ⋅(1:5, reshape(1:25, 5, 5), 2:6) == dot(1:5, reshape(1:25, 5, 5), 2:6)
true
```
