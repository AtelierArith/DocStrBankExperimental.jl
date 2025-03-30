```
<<(x, n)
```

Sol taraftan bit kaydırma operatörü, `x << n`. `n >= 0` için, sonuç `x`'in `n` bit sola kaydırılmasıdır, `0` ile doldurulur. Bu, `x * 2^n` ile eşdeğerdir. `n < 0` için, bu `x >> -n` ile eşdeğerdir.

# Örnekler

```jldoctest
julia> Int8(3) << 2
12

julia> bitstring(Int8(3))
"00000011"

julia> bitstring(Int8(12))
"00001100"
```

Ayrıca bkz. [`>>`](@ref), [`>>>`](@ref), [`exp2`](@ref), [`ldexp`](@ref).
