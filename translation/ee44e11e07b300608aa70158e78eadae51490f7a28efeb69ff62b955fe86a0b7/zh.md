```
precision(num::AbstractFloat; base::Integer=2)
precision(T::Type; base::Integer=2)
```

获取浮点数的精度，定义为有效数字的位数，或浮点类型 `T` 的精度（如果 `T` 是像 [`BigFloat`](@ref) 这样的可变精度类型，则为其当前默认值）。

如果指定了 `base`，则返回该基数下相应的最大有效数字位数。

!!! compat "Julia 1.8"
    `base` 关键字需要至少 Julia 1.8。

