```
DateTime(dt::AbstractString, df::DateFormat=ISODateTimeFormat) -> DateTime
```

`dt` tarih saat dizesini [`DateFormat`](@ref) nesnesinde verilen desene göre ayrıştırarak bir `DateTime` oluşturur veya belirtilmezse dateformat"yyyy-mm-dd\THH:MM:SS.s" kullanır.

`DateTime(::AbstractString, ::AbstractString)` ile benzer, ancak önceden oluşturulmuş bir `DateFormat` nesnesi ile benzer biçimlendirilmiş tarih saat dizelerini tekrar tekrar ayrıştırırken daha verimlidir.
