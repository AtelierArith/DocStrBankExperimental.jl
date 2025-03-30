```
base64decode(string)
```

Base64 kodlu `string`'i çözerek çözümlenen baytların `Vector{UInt8}`'ini döndürür.

Ayrıca [`base64encode`](@ref) bakınız.

# Örnekler

```jldoctest
julia> b = base64decode("SGVsbG8h")
6-element Vector{UInt8}:
 0x48
 0x65
 0x6c
 0x6c
 0x6f
 0x21

julia> String(b)
"Hello!"
```
