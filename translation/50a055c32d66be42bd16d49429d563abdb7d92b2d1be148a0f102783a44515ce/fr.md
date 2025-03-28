```
isvalid(value) -> Bool
```

Retourne `true` si la valeur donnée est valide pour son type, qui peut actuellement être soit `AbstractChar`, soit `String`, soit `SubString{String}`.

# Exemples

```jldoctest
julia> isvalid(Char(0xd800))
false

julia> isvalid(SubString(String(UInt8[0xfe,0x80,0x80,0x80,0x80,0x80]),1,2))
false

julia> isvalid(Char(0xd799))
true
```
