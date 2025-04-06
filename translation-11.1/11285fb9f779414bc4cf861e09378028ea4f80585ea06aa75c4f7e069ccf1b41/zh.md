```
isone(x)
```

如果 `x == one(x)`，则返回 `true`；如果 `x` 是一个数组，则检查 `x` 是否是单位矩阵。

# 示例

```jldoctest
julia> isone(1.0)
true

julia> isone([1 0; 0 2])
false

julia> isone([1 0; 0 true])
true
```
