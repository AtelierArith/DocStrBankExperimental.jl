```
<=(x, y)
≤(x,y)
```

小于或等于比较运算符。回退到 `(x < y) | (x == y)`。

# 示例

```jldoctest
julia> 'a' <= 'b'
true

julia> 7 ≤ 7 ≤ 9
true

julia> "abc" ≤ "abc"
true

julia> 5 <= 3
false
```
