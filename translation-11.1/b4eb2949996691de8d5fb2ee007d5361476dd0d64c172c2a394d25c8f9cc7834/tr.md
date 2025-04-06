```
skip(s, offset)
```

Mevcut konuma göre bir akışı arayın.

# Örnekler

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization.");

julia> seek(io, 5);

julia> skip(io, 10);

julia> read(io, Char)
'G': ASCII/Unicode U+0047 (kategori Lu: Harf, büyük)
```
