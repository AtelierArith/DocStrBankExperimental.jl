```
reinterpret(::Type{Out}, x::In)
```

Ändert die Typinterpretation der Binärdaten im isbits-Wert `x` in die des isbits-Typs `Out`. Die Größe (ohne Padding) von `Out` muss die gleiche sein wie die des Typs von `x`. Zum Beispiel interpretiert `reinterpret(Float32, UInt32(7))` die 4 Bytes, die `UInt32(7)` entsprechen, als [`Float32`](@ref). Beachten Sie, dass `reinterpret(In, reinterpret(Out, x)) === x`

```jldoctest
julia> reinterpret(Float32, UInt32(7))
1.0f-44

julia> reinterpret(NTuple{2, UInt8}, 0x1234)
(0x34, 0x12)

julia> reinterpret(UInt16, (0x34, 0x12))
0x1234

julia> reinterpret(Tuple{UInt16, UInt8}, (0x01, 0x0203))
(0x0301, 0x02)
```

!!! note
    Die Behandlung von Padding unterscheidet sich von reinterpret(::DataType, ::AbstractArray).


!!! warning
    Seien Sie vorsichtig, wenn einige Kombinationen von Bits in `Out` nicht als gültig angesehen werden und andernfalls durch die Konstruktoren und Methoden des Typs verhindert würden. Unerwartetes Verhalten kann ohne zusätzliche Validierung auftreten.

