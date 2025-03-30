```
IOBuffer(string::String)
```

Verilen dizeye dayanan bir yalnızca okunabilir `IOBuffer` oluşturur.

# Örnekler

```jldoctest
julia> io = IOBuffer("Haho");

julia> String(take!(io))
"Haho"

julia> String(take!(io))
"Haho"
```
