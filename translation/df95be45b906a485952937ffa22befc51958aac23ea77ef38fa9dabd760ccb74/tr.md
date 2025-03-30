```
dotu(n, X, incx, Y, incy)
```

İki karmaşık vektör için nokta fonksiyonu, `incx` adımıyla `X` dizisinin `n` elemanını ve `incy` adımıyla `Y` dizisinin `n` elemanını içerir.

# Örnekler

```jldoctest
julia> BLAS.dotu(10, fill(1.0im, 10), 1, fill(1.0+im, 20), 2)
-10.0 + 10.0im
```
