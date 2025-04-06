```
startswith(s::AbstractString, prefix::Regex)
```

`prefix` regex desen `s`'nin başında olup olmadığını kontrol eder ve `true` döner.

!!! not
    `startswith` anchoring'i düzenli ifadeye derlemez, bunun yerine anchoring'i PCRE'ye `match_option` olarak geçirir. Derleme süresi amorti ediliyorsa, `occursin(r"^...", s)` `startswith(s, r"...")`'den daha hızlıdır.


Ayrıca [`occursin`](@ref) ve [`endswith`](@ref) bakınız.

!!! uyumluluk "Julia 1.2"
    Bu yöntem en az Julia 1.2 gerektirir.


# Örnekler

```jldoctest
julia> startswith("JuliaLang", r"Julia|Romeo")
true
```
