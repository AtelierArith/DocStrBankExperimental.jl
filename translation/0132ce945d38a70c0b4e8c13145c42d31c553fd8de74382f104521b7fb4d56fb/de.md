```
bswap(n)
```

Kehrt die Byte-Reihenfolge von `n` um.

(Siehe auch [`ntoh`](@ref) und [`hton`](@ref), um zwischen der aktuellen nativen Byte-Reihenfolge und der Big-Endian-Reihenfolge zu konvertieren.)

# Beispiele

```jldoctest
julia> a = bswap(0x10203040)
0x40302010

julia> bswap(a)
0x10203040

julia> string(1, base = 2)
"1"

julia> string(bswap(1), base = 2)
"100000000000000000000000000000000000000000000000000000000"
```
