```
read(s::IOStream, nb::Integer; all=true)
```

`s`'den en fazla `nb` bayt okuyun ve okunan baytların `Vector{UInt8}`'sini döndürün.

`all` `true` (varsayılan) ise, bu fonksiyon bir hata veya dosya sonu meydana gelene kadar istenen tüm baytları okumaya çalışarak sürekli olarak engellenir. `all` `false` ise, en fazla bir `read` çağrısı yapılır ve döndürülen veri miktarı cihaza bağlıdır. Tüm akış türlerinin `all` seçeneğini desteklemediğini unutmayın.
