```
isreadonly(io) -> Bool
```

Bestimmen Sie, ob ein Stream schreibgeschützt ist.

# Beispiele

```jldoctest
julia> io = IOBuffer("JuliaLang ist eine GitHub-Organisation");

julia> isreadonly(io)
true

julia> io = IOBuffer();

julia> isreadonly(io)
false
```
