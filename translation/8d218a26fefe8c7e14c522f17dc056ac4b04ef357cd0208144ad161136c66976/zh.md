```
isunordered(x)
```

如果 `x` 是一个无法根据 [`<`](@ref) 排序的值，例如 `NaN` 或 `missing`，则返回 `true`。

使用此谓词评估为 `true` 的值可能在其他排序（例如 [`isless`](@ref)）中是可排序的。

!!! compat "Julia 1.7"
    此函数需要 Julia 1.7 或更高版本。

