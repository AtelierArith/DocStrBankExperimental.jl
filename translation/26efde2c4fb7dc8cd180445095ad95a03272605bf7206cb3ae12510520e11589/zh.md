```
dotc(n, X, incx, U, incy)
```

用于两个复数向量的点积函数，由数组 `X` 的 `n` 个元素（步长为 `incx`）和数组 `U` 的 `n` 个元素（步长为 `incy`）组成，对第一个向量进行共轭。

# 示例

```jldoctest
julia> BLAS.dotc(10, fill(1.0im, 10), 1, fill(1.0+im, 20), 2)
10.0 - 10.0im
```
