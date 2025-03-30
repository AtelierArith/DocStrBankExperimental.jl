```
isreadonly(io) -> Bool
```

Bir akışın yalnızca okunabilir olup olmadığını belirleyin.

# Örnekler

```jldoctest
julia> io = IOBuffer("JuliaLang bir GitHub organizasyonudur");

julia> isreadonly(io)
true

julia> io = IOBuffer();

julia> isreadonly(io)
false
```
