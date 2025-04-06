```
nextfloat(x::AbstractFloat)
```

返回与 `x` 相同类型的最小浮点数 `y`，使得 `x < y`。如果不存在这样的 `y`（例如，如果 `x` 是 `Inf` 或 `NaN`），则返回 `x`。

另请参见：[`prevfloat`](@ref)，[`eps`](@ref)，[`issubnormal`](@ref)。
