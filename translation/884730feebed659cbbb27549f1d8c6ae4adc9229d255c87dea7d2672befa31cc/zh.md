```
setprecision([T=BigFloat,] precision::Int; base=2)
```

设置用于 `T` 算术的精度（默认为位数）。如果指定了 `base`，则精度是给定 `base` 中至少提供 `precision` 位所需的最小值。

!!! warning
    此函数不是线程安全的。它将影响所有线程上运行的代码，但如果与使用该设置的计算并发调用，则其行为是未定义的。


!!! compat "Julia 1.8"
    `base` 关键字需要至少 Julia 1.8。

