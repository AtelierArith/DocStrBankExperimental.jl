```
asum(n, X, incx)
```

Dizi `X`'in ilk `n` elemanının büyüklüklerinin `incx` adımıyla toplamı.

Gerçek bir dizi için büyüklük, mutlak değerdir. Karmaşık bir dizi için büyüklük, gerçek kısmın mutlak değeri ile hayali kısmın mutlak değerinin toplamıdır.

# Örnekler

```jldoctest
julia> BLAS.asum(5, fill(1.0im, 10), 2)
5.0

julia> BLAS.asum(2, fill(1.0im, 10), 5)
2.0
```
