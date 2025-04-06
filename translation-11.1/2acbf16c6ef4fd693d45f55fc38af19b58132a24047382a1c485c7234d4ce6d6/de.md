```
bytes2hex(itr) -> String
bytes2hex(io::IO, itr)
```

Konvertiere einen Iterator `itr` von Bytes in seine hexadezimale String-Darstellung, entweder indem ein `String` über `bytes2hex(itr)` zurückgegeben wird oder indem der String in einen `io`-Stream über `bytes2hex(io, itr)` geschrieben wird. Die hexadezimalen Zeichen sind alle klein geschrieben.

!!! compat "Julia 1.7"
    Das Aufrufen von `bytes2hex` mit beliebigen Iteratoren, die `UInt8`-Werte erzeugen, erfordert Julia 1.7 oder höher. In früheren Versionen kannst du den Iterator vor dem Aufruf von `bytes2hex` `collect`-en.


# Beispiele

```jldoctest
julia> a = string(12345, base = 16)
"3039"

julia> b = hex2bytes(a)
2-element Vector{UInt8}:
 0x30
 0x39

julia> bytes2hex(b)
"3039"
```
