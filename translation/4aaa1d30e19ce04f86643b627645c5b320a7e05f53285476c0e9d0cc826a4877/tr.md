```
Time(t::AbstractString, df::DateFormat=ISOTimeFormat) -> Time
```

`Time` nesnesini, belirtilen [`DateFormat`](@ref) nesnesinde verilen deseni izleyerek `t` tarih saat dizesini ayrıştırarak oluşturur veya belirtilmezse tarihformat"HH:MM:SS.s" kullanır.

`Time(::AbstractString, ::AbstractString)` ile benzer, ancak önceden oluşturulmuş bir `DateFormat` nesnesi ile benzer biçimlendirilmiş zaman dizelerini tekrar tekrar ayrıştırırken daha verimlidir.
