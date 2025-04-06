```
base64decode(string)
```

Decodifica la `string` codificada en base64 y devuelve un `Vector{UInt8}` de los bytes decodificados.

Véase también [`base64encode`](@ref).

# Ejemplos

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
