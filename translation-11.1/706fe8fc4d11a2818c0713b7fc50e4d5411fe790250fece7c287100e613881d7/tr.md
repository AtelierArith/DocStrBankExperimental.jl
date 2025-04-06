```
seek(s, pos)
```

Bir akışı verilen konuma yönlendirin.

# Örnekler

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization.");

julia> seek(io, 5);

julia> read(io, Char)
'L': ASCII/Unicode U+004C (kategori Lu: Harf, büyük)
```
