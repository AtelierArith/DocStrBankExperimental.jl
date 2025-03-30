```
ifelse(condition::Bool, x, y)
```

如果 `condition` 为 `true`，则返回 `x`，否则返回 `y`。这与 `?` 或 `if` 的不同之处在于它是一个普通函数，因此所有参数都会先被求值。在某些情况下，使用 `ifelse` 而不是 `if` 语句可以消除生成代码中的分支，并在紧密循环中提供更高的性能。

# 示例

```jldoctest
julia> ifelse(1 > 2, 1, 2)
2
```
