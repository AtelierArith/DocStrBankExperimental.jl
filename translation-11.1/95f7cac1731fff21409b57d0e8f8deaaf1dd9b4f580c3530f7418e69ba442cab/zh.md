```
copysign(x, y) -> z
```

返回 `z`，其大小与 `x` 相同，符号与 `y` 相同。

# 示例

```jldoctest
julia> copysign(1, -2)
-1

julia> copysign(-1, 2)
1
```
