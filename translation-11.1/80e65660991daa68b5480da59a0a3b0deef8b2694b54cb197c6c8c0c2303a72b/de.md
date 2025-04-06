```
hex2bytes(itr)
```

Gibt ein iterierbares `itr` von ASCII-Codes für eine Sequenz von hexadezimalen Ziffern zurück, das ein `Vector{UInt8}` von Bytes entspricht, die der binären Darstellung entsprechen: jedes aufeinanderfolgende Paar von hexadezimalen Ziffern in `itr` gibt den Wert eines Bytes im Rückgabvektor an.

Die Länge von `itr` muss gerade sein, und das zurückgegebene Array hat die Hälfte der Länge von `itr`. Siehe auch [`hex2bytes!`](@ref) für eine In-Place-Version und [`bytes2hex`](@ref) für das Inverse.

!!! compat "Julia 1.7"
    Das Aufrufen von `hex2bytes` mit Iteratoren, die `UInt8`-Werte erzeugen, erfordert Julia 1.7 oder höher. In früheren Versionen können Sie den Iterator vor dem Aufruf von `hex2bytes` `collect`-en.


# Beispiele

```jldoctest
julia> s = string(12345, base = 16)
"3039"

julia> hex2bytes(s)
2-element Vector{UInt8}:
 0x30
 0x39

julia> a = b"01abEF"
6-element Base.CodeUnits{UInt8, String}:
 0x30
 0x31
 0x61
 0x62
 0x45
 0x46

julia> hex2bytes(a)
3-element Vector{UInt8}:
 0x01
 0xab
 0xef
```
