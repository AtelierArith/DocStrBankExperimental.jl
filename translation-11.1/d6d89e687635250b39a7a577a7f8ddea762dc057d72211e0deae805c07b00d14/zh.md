```
asum(n, X, incx)
```

数组 `X` 的前 `n` 个元素的幅度之和，步长为 `incx`。

对于实数数组，幅度是绝对值。对于复数数组，幅度是实部的绝对值与虚部的绝对值之和。

# 示例

```jldoctest
julia> BLAS.asum(5, fill(1.0im, 10), 2)
5.0

julia> BLAS.asum(2, fill(1.0im, 10), 5)
2.0
```
