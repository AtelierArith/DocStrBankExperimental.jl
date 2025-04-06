```
<<(x, n)
```

Linker Bitverschiebungsoperator, `x << n`. Für `n >= 0` ist das Ergebnis `x`, das um `n` Bits nach links verschoben wird, wobei mit `0`s aufgefüllt wird. Dies entspricht `x * 2^n`. Für `n < 0` entspricht dies `x >> -n`.

# Beispiele

```jldoctest
julia> Int8(3) << 2
12

julia> bitstring(Int8(3))
"00000011"

julia> bitstring(Int8(12))
"00001100"
```

Siehe auch [`>>`](@ref), [`>>>`](@ref), [`exp2`](@ref), [`ldexp`](@ref).
