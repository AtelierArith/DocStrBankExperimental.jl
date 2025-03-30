```
RoundingMode
```

Bir tür, kayan nokta işlemlerinin yuvarlama modunu kontrol etmek için ([`rounding`](@ref)/[`setrounding`](@ref) fonksiyonları aracılığıyla) veya en yakın tam sayıya yuvarlama için isteğe bağlı argümanlar olarak ([`round`](@ref) fonksiyonu aracılığıyla) kullanılır.

Şu anda desteklenen yuvarlama modları şunlardır:

  * [`RoundNearest`](@ref) (varsayılan)
  * [`RoundNearestTiesAway`](@ref)
  * [`RoundNearestTiesUp`](@ref)
  * [`RoundToZero`](@ref)
  * [`RoundFromZero`](@ref)
  * [`RoundUp`](@ref)
  * [`RoundDown`](@ref)

!!! compat "Julia 1.9"
    `RoundFromZero`, en az Julia 1.9 gerektirir. Önceki sürümler yalnızca `BigFloat`'lar için `RoundFromZero`'yu destekler.

