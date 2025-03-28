```
unsafe_write(io::IO, ref, nbytes::UInt)
```

Kopiere `nbytes` von `ref` (in einen Zeiger umgewandelt) in das `IO`-Objekt.

Es wird empfohlen, dass Untertypen `T<:IO` die folgende Methodensignatur überschreiben, um effizientere Implementierungen bereitzustellen: `unsafe_write(s::T, p::Ptr{UInt8}, n::UInt)`
