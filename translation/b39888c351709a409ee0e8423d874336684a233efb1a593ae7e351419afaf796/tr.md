```
rem(x, y, r::RoundingMode=RoundToZero)
```

`x`'in `y` ile tam bölümü sonrası kalanını, bölümün `r` yuvarlama moduna göre yuvarlanarak hesaplar. Başka bir deyişle, miktar

```
x - y * round(x / y, r)
```

herhangi bir ara yuvarlama olmadan.

  * eğer `r == RoundNearest` ise, sonuç tamdır ve $[-|y| / 2, |y| / 2]$ aralığındadır. Ayrıca bkz. [`RoundNearest`](@ref).
  * eğer `r == RoundToZero` (varsayılan), o zaman sonuç tamdır ve $[0, |y|)$ aralığındadır eğer `x` pozitifse, aksi takdirde $(-|y|, 0]$ aralığındadır. Ayrıca bkz. [`RoundToZero`](@ref).
  * eğer `r == RoundDown` ise, sonuç $[0, y)$ aralığındadır eğer `y` pozitifse, aksi takdirde $(y, 0]$ aralığındadır. Sonuç, `x` ve `y` farklı işaretlere sahipse ve `abs(x) < abs(y)` ise tam olmayabilir. Ayrıca bkz. [`RoundDown`](@ref).
  * eğer `r == RoundUp` ise, sonuç $(-y, 0]$ aralığındadır eğer `y` pozitifse, aksi takdirde $[0, -y)$ aralığındadır. Sonuç, `x` ve `y` aynı işarete sahipse ve `abs(x) < abs(y)` ise tam olmayabilir. Ayrıca bkz. [`RoundUp`](@ref).
  * eğer `r == RoundFromZero` ise, sonuç $(-y, 0]$ aralığındadır eğer `y` pozitifse, aksi takdirde $[0, -y)$ aralığındadır. Sonuç, `x` ve `y` aynı işarete sahipse ve `abs(x) < abs(y)` ise tam olmayabilir. Ayrıca bkz. [`RoundFromZero`](@ref).

!!! compat "Julia 1.9"
    `RoundFromZero` en az Julia 1.9 gerektirir.


# Örnekler:

```jldoctest
julia> x = 9; y = 4;

julia> x % y  # rem(x, y) ile aynı
1

julia> x ÷ y  # div(x, y) ile aynı
2

julia> x == div(x, y) * y + rem(x, y)
true
```
