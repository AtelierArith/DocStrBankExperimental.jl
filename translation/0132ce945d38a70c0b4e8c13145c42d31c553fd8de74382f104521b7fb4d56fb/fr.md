```
bswap(n)
```

Inverse l'ordre des octets de `n`.

(Voir aussi [`ntoh`](@ref) et [`hton`](@ref) pour convertir entre l'ordre des octets natif actuel et l'ordre big-endian.)

# Exemples

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
