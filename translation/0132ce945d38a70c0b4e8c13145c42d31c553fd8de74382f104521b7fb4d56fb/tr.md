```
bswap(n)
```

`n`'nin bayt sırasını tersine çevirir.

(Ayrıca, mevcut yerel bayt sırası ile büyük-endian sırası arasında dönüştürmek için [`ntoh`](@ref) ve [`hton`](@ref) bakın.)

# Örnekler

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
