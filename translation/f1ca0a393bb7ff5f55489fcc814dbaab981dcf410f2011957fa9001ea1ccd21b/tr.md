```
extrema(itr; [init]) -> (mn, mx)
```

Tek bir geçişte hem minimum `mn` hem de maksimum `mx` öğesini hesaplayın ve bunları 2-tuple olarak döndürün.

Boş `itr` için döndürülen değer `init` ile belirtilebilir. Bu, `min` ve `max` için nötr öğeler olan bir 2-tuple olmalıdır (yani, diğer herhangi bir öğeden büyük/küçük veya eşit olan). Sonuç olarak, `itr` boş olduğunda döndürülen `(mn, mx)` tuple'ı `mn ≥ mx` koşulunu sağlayacaktır. `init` belirtildiğinde, boş olmayan `itr` için bile kullanılabilir.

!!! compat "Julia 1.8"
    Anahtar kelime argümanı `init`, Julia 1.8 veya daha yeni bir sürüm gerektirir.


# Örnekler

```jldoctest
julia> extrema(2:10)
(2, 10)

julia> extrema([9,pi,4.5])
(3.141592653589793, 9.0)

julia> extrema([]; init = (Inf, -Inf))
(Inf, -Inf)
```
