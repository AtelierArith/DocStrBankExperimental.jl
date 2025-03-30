```
copy!(dst, src) -> dst
```

`src`'yi `dst`'ye yerinde [`copy`](@ref) ederek, `dst`'deki mevcut elemanları atar. Eğer `dst` ve `src` aynı türde ise, çağrıdan sonra `dst == src` durumu sağlanmalıdır. Eğer `dst` ve `src` çok boyutlu diziler ise, eşit [`axes`](@ref) olmalıdırlar.

!!! uyarı     Herhangi bir değiştirilmiş argümanın, diğer bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.

Ayrıca bkz. [`copyto!`](@ref).

!!! uyumluluk "Julia 1.1"
    Bu yöntem en az Julia 1.1 gerektirir. Julia 1.0'da bu yöntem `Future` standart kütüphanesinden `Future.copy!` olarak mevcuttur.

