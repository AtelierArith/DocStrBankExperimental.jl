```
ldiv!(Y, A, B) -> Y
```

`A \ B` işlemini yerinde hesaplayın ve sonucu `Y`'ye kaydedin, sonucu döndürün.

`A` argümanı *matris* olmamalıdır. Bunun yerine, matrisler yerine bir faktorizasyon nesnesi olmalıdır (örneğin, [`factorize`](@ref) veya [`cholesky`](@ref) ile üretilmiş). Bunun nedeni, faktorizasyonun hem maliyetli olması hem de genellikle bellek ayırmasıdır (ancak, örneğin, [`lu!`](@ref) ile yerinde de yapılabilir) ve `ldiv!`'ı gerektiren performans kritik durumlar genellikle `A`'nın faktorizasyonu üzerinde ince ayar kontrolü gerektirir.

!!! not
    `Diagonal` ve `UpperTriangular` gibi belirli yapılandırılmış matris türlerine izin verilmektedir, çünkü bunlar zaten faktörize edilmiş bir formdadır.


# Örnekler

```jldoctest
julia> A = [1 2.2 4; 3.1 0.2 3; 4 1 2];

julia> X = [1; 2.5; 3];

julia> Y = zero(X);

julia> ldiv!(Y, qr(A), X);

julia> Y ≈ A\X
true
```
