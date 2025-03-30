```
>>(x, n)
```

Sağ bit kaydırma operatörü, `x >> n`. `n >= 0` için, sonuç `x`'in `n` bit sağa kaydırılmasıdır; `x >= 0` ise `0` ile, `x < 0` ise `1` ile doldurularak `x`'in işareti korunur. Bu, `fld(x, 2^n)` ile eşdeğerdir. `n < 0` için, bu `x << -n` ile eşdeğerdir.

# Örnekler

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

Ayrıca [`>>>`](@ref), [`<<`](@ref) bakınız.
