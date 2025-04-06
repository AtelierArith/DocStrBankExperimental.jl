```
atan(y)
atan(y, x)
```

`y` veya `y/x`'nin ters tanjantını hesaplayın.

Bir gerçek argüman için, bu, pozitif *x*-ekseni ile (1, *y*) noktası arasındaki açıdır ve $[-\pi/2, \pi/2]$ aralığında bir değer döndürür.

İki argüman için, bu, pozitif *x*-ekseni ile (*x*, *y*) noktası arasındaki açıdır ve $[-\pi, \pi]$ aralığında bir değer döndürür. Bu, standart [`atan2`](https://en.wikipedia.org/wiki/Atan2) fonksiyonuna karşılık gelir. Not edin ki, geleneksel olarak `atan(0.0,x)` değeri $\pi$ olarak tanımlanır ve `atan(-0.0,x)` değeri `x < 0` olduğunda $-\pi$ olarak tanımlanır.

Ayrıca [`atand`](@ref) için dereceleri kontrol edin.

# Örnekler

```jldoctest
julia> rad2deg(atan(-1/√3))
-30.000000000000004

julia> rad2deg(atan(-1, √3))
-30.000000000000004

julia> rad2deg(atan(1, -√3))
150.0
```
