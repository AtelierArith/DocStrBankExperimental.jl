```
dot(n, X, incx, Y, incy)
```

两个向量的点积，由数组 `X` 中 `n` 个元素（步幅为 `incx`）和数组 `Y` 中 `n` 个元素（步幅为 `incy`）组成。

# 示例

```jldoctest
julia> BLAS.dot(10, fill(1.0, 10), 1, fill(1.0, 20), 2)
10.0
```
