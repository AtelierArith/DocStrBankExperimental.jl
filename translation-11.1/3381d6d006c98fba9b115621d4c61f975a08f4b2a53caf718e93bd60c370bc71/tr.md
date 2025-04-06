```
reverse(s::AbstractString) -> AbstractString
```

Bir dizeyi tersine çevirir. Teknik olarak, bu işlev bir dizideki kod noktalarını tersine çevirir ve ana kullanımı, özellikle ters düzenli ifade aramaları için ters sıralı dize işleme içindir. `s` içindeki indeksleri `reverse(s)` içindeki indekslere ve tersine dönüştürmek için [`reverseind`](@ref) ve kullanıcı görünür "karakterler" (graphemes) üzerinde işlem yapmak için `Unicode` modülündeki `graphemes`'i de inceleyin. Kopya oluşturmadan ters sıralı yineleme için [`Iterators.reverse`](@ref) de mevcuttur. Özel dize türleri, `reverse` işlevini kendileri uygulamalıdır ve genellikle aynı tür ve kodlama ile bir dize döndürmelidir. Farklı bir kodlama ile bir dize döndürürlerse, `s[reverseind(s,i)] == reverse(s)[i]` koşulunu sağlamak için o dize türü için `reverseind`'i de geçersiz kılmalıdırlar.

# Örnekler

```jldoctest
julia> reverse("JuliaLang")
"gnaLailuJ"
```

!!! not
    Aşağıdaki örnekler farklı sistemlerde farklı şekilde işlenebilir. Yorumlar, nasıl işlenmeleri gerektiğini belirtir.


Birleştirici karakterler sürpriz sonuçlara yol açabilir:

```jldoctest
julia> reverse("ax̂e") # şapka x'in üzerinde, e'nin üzerinde
"êxa"

julia> using Unicode

julia> join(reverse(collect(graphemes("ax̂e")))) # graphemes'i tersine çevirir; şapka x'in üzerinde hem girişte hem de çıkışta
"ex̂a"
```
