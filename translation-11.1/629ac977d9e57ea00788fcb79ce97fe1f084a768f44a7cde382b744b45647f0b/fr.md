```
base64decode(string)
```

Décode la chaîne `string` encodée en base64 et renvoie un `Vector{UInt8}` des octets décodés.

Voir aussi [`base64encode`](@ref).

# Exemples

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
