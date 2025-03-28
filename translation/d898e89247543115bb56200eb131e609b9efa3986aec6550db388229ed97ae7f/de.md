```
>>(x, n)
```

Rechter Bitverschiebungsoperator, `x >> n`. Für `n >= 0` ist das Ergebnis `x`, das um `n` Bits nach rechts verschoben wird, wobei mit `0`s gefüllt wird, wenn `x >= 0`, und mit `1`s, wenn `x < 0`, wobei das Vorzeichen von `x` beibehalten wird. Dies entspricht `fld(x, 2^n)`. Für `n < 0` entspricht dies `x << -n`.

# Beispiele

```jldoctest
julia> Int8(13) >> 2
3

julia> bitstring(Int8(13))
"00001101"

julia> bitstring(Int8(3))
"00000011"

julia> Int8(-14) >> 2
-4

julia> bitstring(Int8(-14))
"11110010"

julia> bitstring(Int8(-4))
"11111100"
```

Siehe auch [`>>>`](@ref), [`<<`](@ref).
