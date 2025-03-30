```
rdiv!(A, B)
```

`A / B` işlemini yerinde hesaplar ve sonucu saklamak için `A`'yı günceller.

`B` argümanı bir matris *olmamalıdır*. Bunun yerine, matrisler yerine bir faktorizasyon nesnesi (örneğin, [`factorize`](@ref) veya [`cholesky`](@ref) ile üretilmiş) olmalıdır. Bunun nedeni, faktorizasyonun hem pahalı olması hem de genellikle bellek ayırmasıdır (ancak, örneğin, [`lu!`](@ref) aracılığıyla yerinde de yapılabilir) ve `rdiv!` gerektiren performans kritik durumlar genellikle `B`'nin faktorizasyonu üzerinde ince ayar kontrolü gerektirir.

!!! not
    `Diagonal` ve `UpperTriangular` gibi belirli yapılandırılmış matris türlerine izin verilmektedir, çünkü bunlar zaten faktörize edilmiş bir formdadır.

