```
modf(x)
```

返回一个元组 `(fpart, ipart)`，包含一个数字的分数部分和整数部分。两个部分与参数具有相同的符号。

# 示例

```jldoctest
julia> modf(3.5)
(0.5, 3.0)

julia> modf(-3.5)
(-0.5, -3.0)
```
