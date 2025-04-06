```
Unicode.julia_chartransform(c::Union{Char,Integer})
```

Unicode karakterini (`Char`) veya kod noktasını (`Integer`) `c`'yi, Julia ayrıştırıcısında kullanılan özel eşdeğerliğe göre karşılık gelen "eşdeğer" karakter veya kod noktasına eşleştirir (NFC normalizasyonuna ek olarak).

Örneğin, `'µ'` (U+00B5 mikro) Julia'nın ayrıştırıcısı tarafından `'μ'` (U+03BC mu) ile eşdeğer olarak kabul edilir, bu nedenle `julia_chartransform` bu dönüşümü gerçekleştirirken diğer karakterleri değiştirmeden bırakır:

```jldoctest
julia> Unicode.julia_chartransform('µ')
'μ': Unicode U+03BC (kategori Ll: Harf, küçük)

julia> Unicode.julia_chartransform('x')
'x': ASCII/Unicode U+0078 (kategori Ll: Harf, küçük)
```

`julia_chartransform`, Julia ayrıştırıcısının kullandığı normalizasyonu taklit etmek için [`Unicode.normalize`](@ref) fonksiyonuna geçmek için esasen faydalıdır:

```jldoctest
julia> s = "µö"
"µö"

julia> s2 = Unicode.normalize(s, compose=true, stable=true, chartransform=Unicode.julia_chartransform)
"μö"

julia> collect(s2)
2-element Vector{Char}:
 'μ': Unicode U+03BC (kategori Ll: Harf, küçük)
 'ö': Unicode U+00F6 (kategori Ll: Harf, küçük)

julia> s2 == string(Meta.parse(s))
true
```

!!! compat "Julia 1.8"
    Bu fonksiyon Julia 1.8'de tanıtılmıştır.

