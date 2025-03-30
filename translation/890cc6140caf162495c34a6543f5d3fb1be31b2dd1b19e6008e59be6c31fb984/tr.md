```
!(x)
```

Boolean değil. [`missing`](@ref) döndürerek [üç değerli mantık](https://en.wikipedia.org/wiki/Three-valued_logic) uygular, eğer `x` `missing` ise.

Ayrıca [`~`](@ref) bit düzeyinde değil için bakınız.

# Örnekler

```jldoctest
julia> !true
false

julia> !false
true

julia> !missing
missing

julia> .![true false true]
1×3 BitMatrix:
 0  1  0
```
