```
cumsum!(B, A; dims::Integer)
```

对 `A` 沿着维度 `dims` 进行累积求和，将结果存储在 `B` 中。另见 [`cumsum`](@ref)。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。

