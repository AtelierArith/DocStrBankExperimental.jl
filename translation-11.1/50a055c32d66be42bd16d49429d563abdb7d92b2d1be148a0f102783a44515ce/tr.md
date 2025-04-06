```
isvalid(value) -> Bool
```

Verilen değerin türü için geçerli olup olmadığını kontrol eder, bu tür şu anda ya `AbstractChar` ya da `String` ya da `SubString{String}` olabilir.

# Örnekler

```jldoctest
julia> isvalid(Char(0xd800))
false

julia> isvalid(SubString(String(UInt8[0xfe,0x80,0x80,0x80,0x80,0x80]),1,2))
false

julia> isvalid(Char(0xd799))
true
```
