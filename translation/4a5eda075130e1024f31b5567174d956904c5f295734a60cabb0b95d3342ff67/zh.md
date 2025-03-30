```
>=(x, y)
≥(x,y)
```

大于或等于比较运算符。回退到 `y <= x`。

# 示例

```jldoctest
julia> 'a' >= 'b'
false

julia> 7 ≥ 7 ≥ 3
true

julia> "abc" ≥ "abc"
true

julia> 5 >= 3
true
```
