```
!(x)
```

Negación booleana. Implementa [lógica de tres valores](https://en.wikipedia.org/wiki/Three-valued_logic), devolviendo [`missing`](@ref) si `x` es `missing`.

Véase también [`~`](@ref) para negación a nivel de bits.

# Ejemplos

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
