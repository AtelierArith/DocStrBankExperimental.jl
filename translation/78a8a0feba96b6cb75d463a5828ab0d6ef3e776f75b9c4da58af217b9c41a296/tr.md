```
startswith(prefix)
```

`prefix` ile başlayan bir argümanın olup olmadığını kontrol eden bir fonksiyon oluşturun, yani `y -> startswith(y, prefix)` fonksiyonuna eşdeğer bir fonksiyon.

Dönen fonksiyon `Base.Fix2{typeof(startswith)}` türündedir ve özel yöntemleri uygulamak için kullanılabilir.

!!! compat "Julia 1.5"
    Tek argüman `startswith(prefix)` en az Julia 1.5 gerektirir.


# Örnekler

```jldoctest
julia> startswith("Julia")("JuliaLang")
true

julia> startswith("Julia")("Ends with Julia")
false
```
