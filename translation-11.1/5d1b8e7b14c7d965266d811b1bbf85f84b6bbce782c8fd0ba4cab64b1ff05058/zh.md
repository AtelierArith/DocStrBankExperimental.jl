```
maxintfloat(T=Float64)
```

在给定的浮点类型 `T`（默认为 `Float64`）中，精确表示的最大连续整数值浮点数。

也就是说，`maxintfloat` 返回最小的正整数值浮点数 `n`，使得 `n+1` 在类型 `T` 中*不能*被精确表示。

当需要 `Integer` 类型的值时，请使用 `Integer(maxintfloat(T))`。
