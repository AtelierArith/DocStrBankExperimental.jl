```
setindex!(A, X, inds...)
A[inds...] = X
```

Dizi `X`'den değerleri, `inds` ile belirtilen `A`'nın bir alt kümesine yerleştirir. `A[inds...] = X` sözdizimi, `(setindex!(A, X, inds...); X)` ile eşdeğerdir.

!!! uyarı     Herhangi bir değiştirilmiş argümanın, başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.

# Örnekler

```jldoctest
julia> A = zeros(2,2);

julia> setindex!(A, [10, 20], [1, 2]);

julia> A[[3, 4]] = [30, 40];

julia> A
2×2 Matrix{Float64}:
 10.0  30.0
 20.0  40.0
```
