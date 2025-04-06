```
rem2pi(x, r::RoundingMode)
```

`x`'in tam sayısal bölümü sonrası kalanını `2π` ile hesaplar, bölüm `r` yuvarlama moduna göre yuvarlanır. Diğer bir deyişle, miktar

```
x - 2π*round(x/(2π),r)
```

herhangi bir ara yuvarlama olmadan. Bu, dahili olarak 2π'nin yüksek hassasiyetli bir yaklaşımını kullanır ve bu nedenle `rem(x,2π,r)`'den daha doğru bir sonuç verir.

  * eğer `r == RoundNearest` ise, sonuç $[-π, π]$ aralığındadır. Bu genellikle en doğru sonuç olacaktır. Ayrıca bkz. [`RoundNearest`](@ref).
  * eğer `r == RoundToZero` ise, sonuç pozitifse $[0, 2π]$ aralığındadır, aksi takdirde $[-2π, 0]$ aralığındadır. Ayrıca bkz. [`RoundToZero`](@ref).
  * eğer `r == RoundDown` ise, sonuç $[0, 2π]$ aralığındadır. Ayrıca bkz. [`RoundDown`](@ref).
  * eğer `r == RoundUp` ise, sonuç $[-2π, 0]$ aralığındadır. Ayrıca bkz. [`RoundUp`](@ref).

# Örnekler

```jldoctest
julia> rem2pi(7pi/4, RoundNearest)
-0.7853981633974485

julia> rem2pi(7pi/4, RoundDown)
5.497787143782138
```
