```
isreadonly(io) -> Bool
```

Déterminez si un flux est en lecture seule.

# Exemples

```jldoctest
julia> io = IOBuffer("JuliaLang est une organisation GitHub");

julia> isreadonly(io)
true

julia> io = IOBuffer();

julia> isreadonly(io)
false
```
