```
<(x, y)
```

小于比较运算符。回退到 [`isless`](@ref)。由于浮点 NaN 值的行为，此运算符实现了部分顺序。

# 实现

具有规范部分顺序的新类型应为新类型的两个参数实现此函数。具有规范全序的新类型应实现 [`isless`](@ref)。

另见 [`isunordered`](@ref)。

# 示例

```jldoctest
julia> 'a' < 'b'
true

julia> "abc" < "abd"
true

julia> 5 < 3
false
```
