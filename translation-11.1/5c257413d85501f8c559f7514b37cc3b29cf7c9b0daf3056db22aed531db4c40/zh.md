```
cumprod!(B, A; dims::Integer)
```

沿着维度 `dims` 计算 `A` 的累积乘积，并将结果存储在 `B` 中。另见 [`cumprod`](@ref)。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。

