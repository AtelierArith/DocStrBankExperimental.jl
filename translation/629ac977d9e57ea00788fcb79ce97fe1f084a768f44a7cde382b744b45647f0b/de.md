```
base64decode(string)
```

Dekodiert den base64-kodierten `string` und gibt einen `Vector{UInt8}` der dekodierten Bytes zurück.

Siehe auch [`base64encode`](@ref).

# Beispiele

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
