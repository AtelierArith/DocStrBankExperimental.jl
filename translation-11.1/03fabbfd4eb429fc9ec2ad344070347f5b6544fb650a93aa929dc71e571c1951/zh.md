```
get_zero_subnormals() -> Bool
```

如果对非标准浮点值（“非正规数”）的操作遵循 IEEE 算术规则，则返回 `false`；如果它们可能被转换为零，则返回 `true`。

!!! warning
    此函数仅影响当前线程。

