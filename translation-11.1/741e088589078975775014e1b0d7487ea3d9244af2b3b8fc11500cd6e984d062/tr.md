```
endswith(suffix)
```

Bir argümanın `suffix` ile bitip bitmediğini kontrol eden bir fonksiyon oluşturun, yani `y -> endswith(y, suffix)` fonksiyonuna eşdeğer bir fonksiyon.

Dönen fonksiyon `Base.Fix2{typeof(endswith)}` türündedir ve özel yöntemleri uygulamak için kullanılabilir.

!!! compat "Julia 1.5"
    Tek argümanlı `endswith(suffix)` en az Julia 1.5 gerektirir.


# Örnekler

```jldoctest
julia> endswith("Julia")("Ends with Julia")
true

julia> endswith("Julia")("JuliaLang")
false
```
