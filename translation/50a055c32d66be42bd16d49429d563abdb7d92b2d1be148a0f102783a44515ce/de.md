```
isvalid(value) -> Bool
```

Gibt `true` zurück, wenn der angegebene Wert für seinen Typ gültig ist, der derzeit entweder `AbstractChar` oder `String` oder `SubString{String}` sein kann.

# Beispiele

```jldoctest
julia> isvalid(Char(0xd800))
false

julia> isvalid(SubString(String(UInt8[0xfe,0x80,0x80,0x80,0x80,0x80]),1,2))
false

julia> isvalid(Char(0xd799))
true
```
