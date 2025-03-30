```
copyto!(dest::AbstractMatrix, src::UniformScaling)
```

将 [`UniformScaling`](@ref) 复制到矩阵上。

!!! compat "Julia 1.1"
    在 Julia 1.0 中，此方法仅支持方形目标矩阵。Julia 1.1 添加了对矩形矩阵的支持。

