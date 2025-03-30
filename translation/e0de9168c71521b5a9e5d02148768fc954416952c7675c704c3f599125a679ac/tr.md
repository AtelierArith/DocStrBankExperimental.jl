```
empty(a::AbstractDict, [index_type=keytype(a)], [value_type=valtype(a)])
```

Boş bir `AbstractDict` konteyneri oluşturur; bu konteyner `index_type` türünde indeksler ve `value_type` türünde değerler kabul edebilir. İkinci ve üçüncü argüman isteğe bağlıdır ve sırasıyla girişin `keytype` ve `valtype` değerlerine varsayılan olarak ayarlanır. (Eğer yalnızca iki türden biri belirtilirse, bu `value_type` olarak varsayılır ve `index_type` için varsayılan olarak `keytype(a)` alınır).

Özel `AbstractDict` alt türleri, belirli indeks ve değer türleri için en uygun sözlük türünü döndürmek üzere üç argümanlı imzayı özelleştirerek seçebilir. Varsayılan olarak boş bir `Dict` döndürülür.
