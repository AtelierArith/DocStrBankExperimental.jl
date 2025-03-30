```
pozisyon(lar)
```

Akışın mevcut pozisyonunu alır.

# Örnekler

```jldoctest
julia> io = IOBuffer("JuliaLang bir GitHub organizasyonudur.");

julia> seek(io, 5);

julia> position(io)
5

julia> skip(io, 10);

julia> position(io)
15

julia> seekend(io);

julia> position(io)
35
```
