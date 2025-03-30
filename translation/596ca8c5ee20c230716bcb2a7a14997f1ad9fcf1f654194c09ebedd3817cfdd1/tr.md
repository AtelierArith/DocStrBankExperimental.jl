```
readbytes!(stream::IO, b::AbstractVector{UInt8}, nb=length(b))
```

`stream`'den en fazla `nb` bayt okuyarak `b`'ye yazar, okunan bayt sayısını döner. `b`'nin boyutu gerektiğinde artırılacaktır (yani, `nb` `length(b)`'den büyükse ve yeterli bayt okunabiliyorsa), ancak asla azaltılmayacaktır.
