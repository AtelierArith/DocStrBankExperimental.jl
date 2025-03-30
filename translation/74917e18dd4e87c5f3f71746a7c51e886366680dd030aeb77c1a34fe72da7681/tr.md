```
RowNonZero
```

Kalan sıfır olmayan ilk eleman, kalan satırlarda pivot eleman olarak seçilir.

Kayan nokta matrisleri için, elde edilen LU algoritması sayısal olarak kararsızdır — bu strateji esasen el hesaplamalarıyla (genellikle bu stratejiyi kullanan) veya yuvarlama hatalarına duyarlı olmayan diğer cebirsel türlerle (örneğin, rasyonel sayılar) karşılaştırma için faydalıdır. Aksi takdirde, Gauss eliminasyonunda genellikle varsayılan `RowMaximum` pivotlama stratejisi tercih edilmelidir.

Matrisin [eleman türü](@ref eltype) bir [`iszero`](@ref) yöntemini kabul etmelidir.
