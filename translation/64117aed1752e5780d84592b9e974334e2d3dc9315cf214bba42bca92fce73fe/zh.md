```
nrm2(n, X, incx)
```

由数组 `X` 中 `n` 个元素组成的向量的 2-范数，步长为 `incx`。

# 示例

```jldoctest
julia> BLAS.nrm2(4, fill(1.0, 8), 2)
2.0

julia> BLAS.nrm2(1, fill(1.0, 8), 2)
1.0
```
