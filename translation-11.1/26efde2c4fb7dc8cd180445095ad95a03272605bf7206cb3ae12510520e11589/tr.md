```
dotc(n, X, incx, U, incy)
```

İki karmaşık vektör için Dot fonksiyonu, `incx` adımıyla `X` dizisinin `n` elemanını ve `incy` adımıyla `U` dizisinin `n` elemanını alır, ilk vektörü konjuge eder.

# Örnekler

```jldoctest
julia> BLAS.dotc(10, fill(1.0im, 10), 1, fill(1.0+im, 20), 2)
10.0 - 10.0im
```
