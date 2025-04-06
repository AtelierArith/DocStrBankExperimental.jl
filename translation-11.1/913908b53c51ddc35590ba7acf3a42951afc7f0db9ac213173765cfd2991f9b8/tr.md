```
round([T,] x, [r::RoundingMode])
round(x, [r::RoundingMode]; digits::Integer=0, base = 10)
round(x, [r::RoundingMode]; sigdigits::Integer, base = 10)
```

`x` sayısını yuvarlar.

Anahtar kelime argümanları olmadan, `x` bir tam sayı değerine yuvarlanır ve bir `T` türünde veya `T` sağlanmadıysa `x` ile aynı türde bir değer döner. Eğer değer `T` tarafından temsil edilemeyecekse, [`InexactError`](@ref) hatası fırlatılacaktır, bu da [`convert`](@ref) ile benzerdir.

`digits` anahtar kelime argümanı sağlanırsa, belirtilen ondalık basamağı (veya negatifse öncesini) yuvarlar, `base` tabanında.

`sigdigits` anahtar kelime argümanı sağlanırsa, belirtilen anlamlı basamak sayısına yuvarlar, `base` tabanında.

[`RoundingMode`](@ref) `r`, yuvarlama yönünü kontrol eder; varsayılan [`RoundNearest`](@ref) olup, en yakın tam sayıya yuvarlar, 0.5 olan bağlama değerleri en yakın çift tam sayıya yuvarlanır. `round`'un küresel yuvarlama modu değişirse yanlış sonuçlar verebileceğini unutmayın (bkz. [`rounding`](@ref)).

Bir kayan nokta türüne yuvarlarken, o tür tarafından temsil edilebilen (ve Inf) tam sayılara yuvarlanır, gerçek tam sayılara değil. Inf, "en yakın" belirlemek için `floatmax(T)`'den bir ulp daha büyük olarak kabul edilir, bu da [`convert`](@ref) ile benzerdir.

# Örnekler

```jldoctest
julia> round(1.7)
2.0

julia> round(Int, 1.7)
2

julia> round(1.5)
2.0

julia> round(2.5)
2.0

julia> round(pi; digits=2)
3.14

julia> round(pi; digits=3, base=2)
3.125

julia> round(123.456; sigdigits=2)
120.0

julia> round(357.913; sigdigits=4, base=2)
352.0

julia> round(Float16, typemax(UInt128))
Inf16

julia> floor(Float16, typemax(UInt128))
Float16(6.55e4)
```

!!! not
    İkili kayan nokta sayıları üzerinde çalışırken, 2 dışındaki tabanlarda belirtilen basamaklara yuvarlama kesin olmayabilir. Örneğin, `1.15` değerini temsil eden [`Float64`](@ref) aslında 1.15'ten *daha küçüktür*, ancak 1.2'ye yuvarlanacaktır. Örneğin:

    ```jldoctest
    julia> x = 1.15
    1.15

    julia> big(1.15)
    1.149999999999999911182158029987476766109466552734375

    julia> x < 115//100
    true

    julia> round(x, digits=1)
    1.2
    ```


# Uzantılar

`round`'u yeni sayısal türlere genişletmek için, genellikle `Base.round(x::NewType, r::RoundingMode)` tanımlamak yeterlidir.
