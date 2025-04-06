```
Date(d::AbstractString, df::DateFormat=ISODateFormat) -> Date
```

`d` tarih dizesini [`DateFormat`](@ref) nesnesinde belirtilen desene göre ayrıştırarak bir `Date` oluşturur veya belirtilmezse tarihformat"yyyy-mm-dd" kullanır.

`Date(::AbstractString, ::AbstractString)` ile benzer, ancak önceden oluşturulmuş bir `DateFormat` nesnesi ile benzer biçimlendirilmiş tarih dizelerini tekrar tekrar ayrıştırırken daha verimlidir.
