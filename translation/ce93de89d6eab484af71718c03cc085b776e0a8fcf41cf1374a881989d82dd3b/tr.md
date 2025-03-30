```
endswith(s::AbstractString, suffix::Regex)
```

`true` döndürür eğer `s`, regex deseni `suffix` ile bitiyorsa.

!!! not
    `endswith`, sabitlemeyi düzenli ifadeye derlemez, bunun yerine sabitlemeyi `match_option` olarak PCRE'ye geçirir. Derleme süresi amorti ediliyorsa, `occursin(r"...$", s)` `endswith(s, r"...")`'den daha hızlıdır.


Ayrıca bkz. [`occursin`](@ref) ve [`startswith`](@ref).

!!! uyumluluk "Julia 1.2"
    Bu yöntem en az Julia 1.2 gerektirir.


# Örnekler

```jldoctest
julia> endswith("JuliaLang", r"Lang|Roberts")
true
```
