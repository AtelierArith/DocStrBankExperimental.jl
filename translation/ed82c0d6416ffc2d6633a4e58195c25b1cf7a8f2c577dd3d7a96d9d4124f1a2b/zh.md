```
flipsign(x, y)
```

如果 `y` 为负，则返回 `x` 的符号翻转。例如 `abs(x) = flipsign(x,x)`。

# 示例

```jldoctest
julia> flipsign(5, 3)
5

julia> flipsign(5, -3)
-5
```
