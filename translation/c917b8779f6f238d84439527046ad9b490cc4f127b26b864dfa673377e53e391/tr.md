```
issuccess(F::Factorization)
```

Bir matrisin faktorizasyonunun başarılı olup olmadığını test eder.

!!! uyum "Julia 1.6"
    `issuccess(::CholeskyPivoted)` Julia 1.6 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> F = cholesky([1 0; 0 1]);

julia> issuccess(F)
true
```
