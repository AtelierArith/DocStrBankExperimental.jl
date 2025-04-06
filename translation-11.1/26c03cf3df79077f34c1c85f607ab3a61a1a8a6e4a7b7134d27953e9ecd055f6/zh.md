```
prevfloat(x::AbstractFloat)
```

返回与 `x` 相同类型的最大浮点数 `y`，使得 `y < x`。如果不存在这样的 `y`（例如，如果 `x` 是 `-Inf` 或 `NaN`），则返回 `x`。
