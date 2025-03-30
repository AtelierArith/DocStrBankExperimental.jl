```
soyut tür
```

`soyut tür` bir türü tanımlar ki bu tür örneklendirilemez ve yalnızca tür grafiğinde bir düğüm olarak hizmet eder, böylece ilişkili somut türlerin kümelerini tanımlar: bunlar, onların soyundan gelen somut türlerdir. Soyut türler, Julia'nın tür sistemini yalnızca bir nesne uygulamaları koleksiyonu olmaktan daha fazlası yapan kavramsal hiyerarşiyi oluşturur. Örneğin:

```julia
soyut tür Sayı son
soyut tür Gerçek <: Sayı son
```

[`Sayı`](@ref) hiçbir süper türe sahip değildir, oysa [`Gerçek`](@ref) `Sayı`nın soyut bir alt türüdür.
