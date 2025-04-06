```
occursin(haystack)
```

`haystack` içinde argümanının geçip geçmediğini kontrol eden bir fonksiyon oluşturun, yani `needle -> occursin(needle, haystack)` fonksiyonuna eşdeğer bir fonksiyon.

Dönen fonksiyon `Base.Fix2{typeof(occursin)}` tipindedir.

!!! compat "Julia 1.6"
    Bu yöntem Julia 1.6 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> search_f = occursin("JuliaLang is a programming language");

julia> search_f("JuliaLang")
true

julia> search_f("Python")
false
```
