```
isapprox(x; kwargs...) / ≈(x; kwargs...)
```

创建一个函数，该函数使用 `≈` 将其参数与 `x` 进行比较，即一个等价于 `y -> y ≈ x` 的函数。

这里支持的关键字参数与 2 个参数的 `isapprox` 中的相同。

!!! compat "Julia 1.5"
    此方法需要 Julia 1.5 或更高版本。

