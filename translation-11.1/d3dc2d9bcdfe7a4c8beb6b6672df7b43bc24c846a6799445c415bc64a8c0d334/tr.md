```
readbytes!(stream::IOStream, b::AbstractVector{UInt8}, nb=length(b); all::Bool=true)
```

`stream`'den `b`'ye en fazla `nb` bayt okuyun ve okunan bayt sayısını döndürün. `b`'nin boyutu gerektiğinde artırılacaktır (yani `nb`, `length(b)`'den büyükse ve yeterince bayt okunabiliyorsa), ancak asla azaltılmayacaktır.

`all` `true` (varsayılan) ise, bu fonksiyon bir hata veya dosya sonu meydana gelene kadar tüm istenen baytları okumak için tekrar tekrar engellenecektir. `all` `false` ise, en fazla bir `read` çağrısı gerçekleştirilir ve döndürülen veri miktarı cihaza bağlıdır. Tüm akış türlerinin `all` seçeneğini desteklemediğini unutmayın.
