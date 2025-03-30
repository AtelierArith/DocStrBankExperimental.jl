```
peek(stream[, T=UInt8])
```

Bir akıştan mevcut konumu ilerletmeden `T` türünde bir değer okuyun ve döndürün. Ayrıca [`startswith(stream, char_or_string)`](@ref) bakın.

# Örnekler

```jldoctest
julia> b = IOBuffer("julia");

julia> peek(b)
0x6a

julia> position(b)
0

julia> peek(b, Char)
'j': ASCII/Unicode U+006A (kategori Ll: Küçük harf, harf)
```

!!! compat "Julia 1.5"
    Bir tür kabul eden yöntem, Julia 1.5 veya daha yenisini gerektirir.

