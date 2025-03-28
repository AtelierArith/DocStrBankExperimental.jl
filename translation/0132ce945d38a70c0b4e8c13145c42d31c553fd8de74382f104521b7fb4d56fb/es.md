```
bswap(n)
```

Invierte el orden de los bytes de `n`.

(Véase también [`ntoh`](@ref) y [`hton`](@ref) para convertir entre el orden de bytes nativo actual y el orden big-endian.)

# Ejemplos

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
