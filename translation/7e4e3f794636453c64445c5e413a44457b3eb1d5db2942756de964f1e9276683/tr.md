```
IOBuffer([data::AbstractVector{UInt8}]; keywords...) -> IOBuffer
```

Önceden var olan bir dizi üzerinde isteğe bağlı olarak çalışabilen, bellek içi bir G/Ç akışı oluşturur.

İsteğe bağlı anahtar kelime argümanlarını alabilir:

  * `read`, `write`, `append`: işlemleri tamponla sınırlamak için; ayrıntılar için `open`'a bakın.
  * `truncate`: tampon boyutunu sıfır uzunluğa kısaltır.
  * `maxsize`: tamponun büyüyemeyeceği bir boyut belirtir.
  * `sizehint`: tamponun kapasitesini önerir (`data` `sizehint!(data, size)`'i uygulamalıdır).

`data` verilmediğinde, tampon varsayılan olarak hem okunabilir hem de yazılabilir olacaktır.

# Örnekler

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang is a GitHub organization.", " It has many members.")
56

julia> String(take!(io))
"JuliaLang is a GitHub organization. It has many members."

julia> io = IOBuffer(b"JuliaLang is a GitHub organization.")
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=35, maxsize=Inf, ptr=1, mark=-1)

julia> read(io, String)
"JuliaLang is a GitHub organization."

julia> write(io, "This isn't writable.")
HATA: ArgumentError: ensureroom failed, IOBuffer is not writeable

julia> io = IOBuffer(UInt8[], read=true, write=true, maxsize=34)
IOBuffer(data=UInt8[...], readable=true, writable=true, seekable=true, append=false, size=0, maxsize=34, ptr=1, mark=-1)

julia> write(io, "JuliaLang is a GitHub organization.")
34

julia> String(take!(io))
"JuliaLang is a GitHub organization"

julia> length(read(IOBuffer(b"data", read=true, truncate=false)))
4

julia> length(read(IOBuffer(b"data", read=true, truncate=true)))
0
```
