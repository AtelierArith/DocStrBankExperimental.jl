```
dot(n, X, incx, Y, incy)
```

2つのベクトルのドット積で、配列 `X` の `n` 要素とストライド `incx`、配列 `Y` の `n` 要素とストライド `incy` から成ります。

# 例

```jldoctest
julia> BLAS.dot(10, fill(1.0, 10), 1, fill(1.0, 20), 2)
10.0
```
