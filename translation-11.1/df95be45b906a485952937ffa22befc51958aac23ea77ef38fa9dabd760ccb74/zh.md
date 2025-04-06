```
dotu(n, X, incx, Y, incy)
```

用于两个复数向量的点积函数，包含 `n` 个元素的数组 `X`，步长为 `incx`，以及 `n` 个元素的数组 `Y`，步长为 `incy`。

# 示例

```jldoctest
julia> BLAS.dotu(10, fill(1.0im, 10), 1, fill(1.0+im, 20), 2)
-10.0 + 10.0im
```
