```
graphemes(s::AbstractString, m:n) -> SubString
```

`S`'nin `m`-inci ile `n`-inci graphemlerinden oluşan bir [`SubString`](@ref) döndürür. Burada ikinci argüman `m:n` tam sayı değerli bir [`AbstractUnitRange`](@ref) dir.

Gevşek bir şekilde, bu, dizgedeki `m:n`-inci kullanıcı tarafından algılanan "karakterler" ile ilgilidir. Örneğin:

```jldoctest
julia> s = graphemes("exposé", 3:6)
"posé"

julia> collect(s)
5-element Vector{Char}:
 'p': ASCII/Unicode U+0070 (category Ll: Letter, lowercase)
 'o': ASCII/Unicode U+006F (category Ll: Letter, lowercase)
 's': ASCII/Unicode U+0073 (category Ll: Letter, lowercase)
 'e': ASCII/Unicode U+0065 (category Ll: Letter, lowercase)
 '́': Unicode U+0301 (category Mn: Mark, nonspacing)
```

Bu, `"exposé"` içindeki 3. ile *7.* kod noktalarını ([`Char`](@ref)s) içerir, çünkü `"é"` graphemi aslında *iki* Unicode kod noktasından oluşur (bir `'e'` ve ardından bir akut aksan birleştirme karakteri U+0301).

Graphem sınırlarını bulmak, dizge içeriği üzerinde yineleme gerektirdiğinden, `graphemes(s, m:n)` fonksiyonu, alt dizenin sonuna kadar olan dizge uzunluğuna (kod noktası sayısına) orantılı bir zaman gerektirir.

!!! compat "Julia 1.9"
    `graphemes`'in `m:n` argümanı Julia 1.9'u gerektirir.

