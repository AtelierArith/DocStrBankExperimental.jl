```
x | y
```

Bitwise veya. [Üç değerli mantık](https://en.wikipedia.org/wiki/Three-valued_logic) uygular, bir operand `missing` ve diğeri `false` ise [`missing`](@ref) döner.

Ayrıca bakınız: [`&`](@ref), [`xor`](@ref), [`||`](@ref).

# Örnekler

```jldoctest
julia> 4 | 10
14

julia> 4 | 1
5

julia> true | missing
true

julia> false | missing
missing
```
