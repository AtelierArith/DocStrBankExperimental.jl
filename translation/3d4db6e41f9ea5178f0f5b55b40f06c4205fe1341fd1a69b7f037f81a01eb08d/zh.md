```
count([f=identity,] itr; init=0) -> Integer
```

计算在 `itr` 中函数 `f` 返回 `true` 的元素数量。如果省略 `f`，则计算 `itr` 中 `true` 元素的数量（这应该是一个布尔值集合）。`init` 可选地指定开始计数的值，因此也决定了输出类型。

!!! compat "Julia 1.6"
    `init` 关键字是在 Julia 1.6 中添加的。


另请参见: [`any`](@ref), [`sum`](@ref).

# 示例

```jldoctest
julia> count(i->(4<=i<=6), [2,3,4,5,6])
3

julia> count([true, false, true, true])
3

julia> count(>(3), 1:7, init=0x03)
0x07
```
