```
titlecase(s::AbstractString; [wordsep::Function], strict::Bool=true) -> String
```

`s` içindeki her kelimenin ilk karakterini büyük harfle başlatır; eğer `strict` true ise, diğer tüm karakterler küçük harfe dönüştürülür, aksi takdirde olduğu gibi bırakılır. Varsayılan olarak, yeni bir graphem ile başlayan tüm harf dışı karakterler kelime ayırıcı olarak kabul edilir; hangi karakterlerin kelime ayırıcı olarak kabul edileceğini belirlemek için `wordsep` anahtar kelimesi ile bir predikat geçirilebilir. Sadece `s` içindeki ilk karakteri büyük harfle başlatmak için [`uppercasefirst`](@ref) fonksiyonuna da bakın.

Ayrıca [`uppercase`](@ref), [`lowercase`](@ref), [`uppercasefirst`](@ref) fonksiyonlarına da bakın.

# Örnekler

```jldoctest
julia> titlecase("the JULIA programming language")
"The Julia Programming Language"

julia> titlecase("ISS - international space station", strict=false)
"ISS - International Space Station"

julia> titlecase("a-a b-b", wordsep = c->c==' ')
"A-a B-b"
```
