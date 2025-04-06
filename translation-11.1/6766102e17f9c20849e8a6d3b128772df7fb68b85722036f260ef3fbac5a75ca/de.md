```
unsafe_read(io::IO, ref, nbytes::UInt)
```

Kopiere `nbytes` aus dem `IO`-Stream-Objekt in `ref` (konvertiert in einen Zeiger).

Es wird empfohlen, dass Subtypen `T<:IO` die folgende Methodensignatur überschreiben, um effizientere Implementierungen bereitzustellen: `unsafe_read(s::T, p::Ptr{UInt8}, n::UInt)`
