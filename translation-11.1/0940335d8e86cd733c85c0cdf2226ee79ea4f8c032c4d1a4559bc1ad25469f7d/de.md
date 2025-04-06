```
readavailable(stream)
```

Lese verfügbare gepufferte Daten aus einem Stream. Tatsächliche I/O wird nur durchgeführt, wenn noch keine Daten gepuffert wurden. Das Ergebnis ist ein `Vector{UInt8}`.

!!! warning
    Die Menge der zurückgegebenen Daten ist implementierungsabhängig; sie kann beispielsweise von der internen Wahl der Puffergröße abhängen. Andere Funktionen wie [`read`](@ref) sollten im Allgemeinen stattdessen verwendet werden.

