```
setprecision(f::Function, [T=BigFloat,] precision::Integer; base=2)
```

在 `f` 的持续时间内更改 `T` 的算术精度（在给定的 `base` 中）。这在逻辑上等同于：

```
old = precision(BigFloat)
setprecision(BigFloat, precision)
f()
setprecision(BigFloat, old)
```

通常用作 `setprecision(T, precision) do ... end`

注意：`nextfloat()`、`prevfloat()` 不使用 `setprecision` 提到的精度。

!!! compat "Julia 1.8"
    `base` 关键字需要至少 Julia 1.8。

