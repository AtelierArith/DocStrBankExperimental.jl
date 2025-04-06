```
cumprod!(y::AbstractVector, x::AbstractVector)
```

向量 `x` 的累积乘积，结果存储在 `y` 中。另见 [`cumprod`](@ref)。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。

