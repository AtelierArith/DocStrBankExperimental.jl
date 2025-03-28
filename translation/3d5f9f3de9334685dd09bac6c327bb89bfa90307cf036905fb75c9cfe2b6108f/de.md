```
BitArray{N} <: AbstractArray{Bool, N}
```

Speichereffizientes `N`-dimensionales Boolesches Array, das für jeden Booleschen Wert nur ein Bit verwendet.

`BitArray`s packen bis zu 64 Werte in jede 8 Bytes, was zu einer 8-fachen Speichereffizienz im Vergleich zu `Array{Bool, N}` führt und es ermöglicht, einige Operationen auf 64 Werten gleichzeitig auszuführen.

Standardmäßig gibt Julia `BitArrays` von [Broadcasting](@ref Broadcasting) Operationen zurück, die Boolesche Elemente erzeugen (einschließlich punktierter Vergleiche wie `.==`) sowie von den Funktionen [`trues`](@ref) und [`falses`](@ref).

!!! Hinweis     Aufgrund seines kompakten Speicherformats ist der gleichzeitige Zugriff auf die Elemente eines `BitArray`, bei dem mindestens eines von ihnen ein Schreibzugriff ist, nicht threadsicher.
