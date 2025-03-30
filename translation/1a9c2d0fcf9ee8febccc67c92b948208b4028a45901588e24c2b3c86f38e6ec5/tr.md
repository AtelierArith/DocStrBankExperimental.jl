```
isequal_normalized(s1::AbstractString, s2::AbstractString; casefold=false, stripmark=false, chartransform=identity)
```

`s1` ve `s2`'nin kanonik olarak eşdeğer Unicode dizgeleri olup olmadığını döndürür. Eğer `casefold=true` ise, büyük/küçük harf farkını göz ardı eder (Unicode büyük/küçük harf dönüştürmesi yapar); eğer `stripmark=true` ise, diakritik işaretleri ve diğer birleştirici karakterleri temizler.

[`Unicode.normalize`](@ref) ile olduğu gibi, özel normalizasyonlar gerçekleştirmek için `chartransform` anahtar kelimesi aracılığıyla bir işlev de geçirebilirsiniz ( `Integer` kod noktalarını kod noktalarına eşleyen) , örneğin [`Unicode.julia_chartransform`](@ref).

!!! compat "Julia 1.8"
    `isequal_normalized` işlevi Julia 1.8'de eklendi.


# Örnekler

Örneğin, `"noël"` dizgesi, `"ë"`nin tek bir kod noktası U+00EB'den mi yoksa ASCII karakteri `'e'`nin ardından U+0308 birleştirici-diyaliz karakteri ile mi oluşturulduğuna bağlı olarak Unicode'da iki kanonik olarak eşdeğer şekilde oluşturulabilir.

```jldoctest
julia> s1 = "noël"
"noël"

julia> s2 = "noël"
"noël"

julia> s1 == s2
false

julia> isequal_normalized(s1, s2)
true

julia> isequal_normalized(s1, "noel", stripmark=true)
true

julia> isequal_normalized(s1, "NOËL", casefold=true)
true
```
