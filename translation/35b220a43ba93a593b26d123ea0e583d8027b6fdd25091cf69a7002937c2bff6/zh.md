```
set_zero_subnormals(yes::Bool) -> Bool
```

如果 `yes` 为 `false`，后续的浮点运算将遵循 IEEE 对于次正规值（“非正规数”）的算术规则。否则，浮点运算被允许（但不要求）将次正规输入或输出转换为零。除非 `yes==true` 但硬件不支持将次正规数归零，否则返回 `true`。

`set_zero_subnormals(true)` 可以加速某些硬件上的一些计算。然而，它可能会破坏诸如 `(x-y==0) == (x==y)` 的恒等式。

!!! warning
    此函数仅影响当前线程。

