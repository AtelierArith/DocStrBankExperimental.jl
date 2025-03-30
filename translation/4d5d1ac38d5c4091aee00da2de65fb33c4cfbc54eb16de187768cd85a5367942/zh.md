```
>(x, y)
```

大于比较运算符。回退到 `y < x`。

# 实现

通常，新类型应该实现 [`<`](@ref) 而不是这个函数，并依赖回退定义 `>(x, y) = y < x`。

# 示例

```jldoctest
julia> 'a' > 'b'
false

julia> 7 > 3 > 1
true

julia> "abc" > "abd"
false

julia> 5 > 3
true
```
