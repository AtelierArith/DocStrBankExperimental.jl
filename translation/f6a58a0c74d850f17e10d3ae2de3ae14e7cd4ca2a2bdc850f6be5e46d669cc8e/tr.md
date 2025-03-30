```
skipchars(predicate, io::IO; linecomment=nothing)
```

Akışı `io` öyle bir şekilde ilerletin ki, bir sonraki okunacak karakter, `predicate`'in `false` döndüğü ilk kalan karakter olsun. Eğer `linecomment` anahtar kelime argümanı belirtilmişse, o karakterden başlayarak bir sonraki satırın başına kadar olan tüm karakterler yok sayılır.

# Örnekler

```jldoctest
julia> buf = IOBuffer("    text")
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=8, maxsize=Inf, ptr=1, mark=-1)

julia> skipchars(isspace, buf)
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=8, maxsize=Inf, ptr=5, mark=-1)

julia> String(readavailable(buf))
"text"
```
