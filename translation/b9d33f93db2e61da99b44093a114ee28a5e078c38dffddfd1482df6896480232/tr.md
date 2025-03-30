```
Unicode.isassigned(c) -> Bool
```

Verilen karakter veya tam sayının atanmış bir Unicode kod noktası olup olmadığını kontrol eder. `true` döner.

# Örnekler

```jldoctest
julia> Unicode.isassigned(101)
true

julia> Unicode.isassigned('\x01')
true
```
