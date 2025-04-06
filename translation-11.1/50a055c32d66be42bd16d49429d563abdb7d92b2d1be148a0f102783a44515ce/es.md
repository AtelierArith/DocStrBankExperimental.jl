```
isvalid(value) -> Bool
```

Devuelve `true` si el valor dado es válido para su tipo, que actualmente puede ser `AbstractChar` o `String` o `SubString{String}`.

# Ejemplos

```jldoctest
julia> isvalid(Char(0xd800))
false

julia> isvalid(SubString(String(UInt8[0xfe,0x80,0x80,0x80,0x80,0x80]),1,2))
false

julia> isvalid(Char(0xd799))
true
```
