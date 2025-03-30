```
ldiv!(A, B)
```

`A \ B`'yi yerinde hesaplayarak `B`'yi sonuçla günceller.

`A` argümanı *matris* olmamalıdır. Bunun yerine, matrisler yerine bir faktorizasyon nesnesi olmalıdır (örneğin, [`factorize`](@ref) veya [`cholesky`](@ref) ile üretilmiş). Bunun nedeni, faktorizasyonun hem pahalı olması hem de genellikle bellek ayırmasıdır (ancak, örneğin, [`lu!`](@ref) ile yerinde de yapılabilir) ve `ldiv!`'i gerektiren performans kritik durumlar genellikle `A`'nın faktorizasyonu üzerinde ince ayar kontrolü gerektirir.

!!! not
    `Diagonal` ve `UpperTriangular` gibi belirli yapılandırılmış matris türlerine izin verilmektedir, çünkü bunlar zaten faktörize edilmiş bir formdadır.


# Örnekler

```jldoctest
julia> A = [1 2.2 4; 3.1 0.2 3; 4 1 2];

julia> X = [1; 2.5; 3];

julia> Y = copy(X);

julia> ldiv!(qr(A), X);

julia> X ≈ A\Y
true
```
