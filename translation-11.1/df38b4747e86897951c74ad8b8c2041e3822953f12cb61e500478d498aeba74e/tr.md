```
x & y
```

Bitwise ve. [Üç değerli mantık](https://en.wikipedia.org/wiki/Three-valued_logic) uygular, bir operand `missing` ve diğeri `true` ise [`missing`](@ref) döner. Fonksiyon uygulama biçimi için parantez ekleyin: `(&)(x, y)`.

Ayrıca bkz: [`|`](@ref), [`xor`](@ref), [`&&`](@ref).

# Örnekler

```jldoctest
julia> 4 & 10
0

julia> 4 & 12
4

julia> true & missing
missing

julia> false & missing
false
```
