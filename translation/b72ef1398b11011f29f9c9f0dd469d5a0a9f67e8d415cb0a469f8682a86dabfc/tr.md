```
dot(n, X, incx, Y, incy)
```

İki vektörün nokta çarpımı, `incx` adımıyla `X` dizisinin `n` elemanını ve `incy` adımıyla `Y` dizisinin `n` elemanını içerir.

# Örnekler

```jldoctest
julia> BLAS.dot(10, fill(1.0, 10), 1, fill(1.0, 20), 2)
10.0
```
