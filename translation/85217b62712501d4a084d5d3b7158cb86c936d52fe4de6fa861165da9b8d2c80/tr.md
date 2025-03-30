```
lazy"str"
```

Bir [`LazyString`](@ref) oluşturmak için normal dize interpolasyon sözdizimini kullanın. Interpolasyonların, LazyString oluşturma zamanında *değerlendirildiğini*, ancak dizeye ilk erişim anına kadar *yazdırmanın* ertelendiğini unutmayın.

[`LazyString`](@ref) belgelerine bakarak eşzamanlı programlar için güvenlik özelliklerini inceleyin.

# Örnekler

```
julia> n = 5; str = lazy"n is $n"
"n is 5"

julia> typeof(str)
LazyString
```

!!! compat "Julia 1.8"
    `lazy"str"` Julia 1.8 veya daha yenisini gerektirir.

