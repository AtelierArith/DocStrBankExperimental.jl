```
seekstart(s)
```

Bir akışı başlangıcına yönlendirin.

# Örnekler

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization.");

julia> seek(io, 5);

julia> read(io, Char)
'L': ASCII/Unicode U+004C (kategori Lu: Harf, büyük)

julia> seekstart(io);

julia> read(io, Char)
'J': ASCII/Unicode U+004A (kategori Lu: Harf, büyük)
```
